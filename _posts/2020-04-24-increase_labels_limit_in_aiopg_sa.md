---
id: 796
title: Увеличение максимально длины алисов для полей в SQLAlchemy
date: 2020-04-24T23:28:00+03:00
author: h4
layout: post
permalink: /increase_labels_limit_in_aiopg_sa/
---

Недавно мы решили разнести таблицы в нашей базе по разным схемам, используя их как пространства имён. Так сложилось, что мы не приветсвуем сокращения, поэтому для некоторые таблицы и поля в них были достаточно длинными. Само по себе это не плохо, но *SQLAlchemy*, которую мы используем как *query builder*, использует алиасы для полей таблиц, чтобы избежать конфликта имён. То есть 

```python
sa.select(['id', 'title'], use_labels=True).select_from('my_table')
```

превратится в 

 ```sql
SELECT 
	id AS my_table_id,
  title AS my_table_title
FROM
  my_table
 ```

А при явном указании схемы `my_table_id` заменится на `my_schema_my_table_id`.

Опять же, в алиасах нет ничего плохого, одна польза, если бы не [ограничение Postgres](https://www.postgresql.org/docs/current/sql-syntax-lexical.html#SQL-SYNTAX-IDENTIFIERS) на максимальную длину идентификатора в **63** символа. В итоге алиас `impicit_schema_name_very_specific_table_name_unbeatable_field_name` превращатся при компиляции запроса в `impicit_schema_name_very_specific_table_name_unbeatable_fiel_1` и дальше мы получем ошибку вида 

```
could not locate column in row for column very_specific_table_name.unbeatable_field_name
```

Чтобы обойти это ограничение при использовании чистой SQLAlchemy достаточно добавить аргумент **label_length** [при вызове create_engine()](https://docs.sqlalchemy.org/en/13/core/engines.html#sqlalchemy.create_engine.params.label_length).

Мы используем обёртку aiopg.sa, и там я не нашёл простого способа передать этот параметр, поэтому пришлось вручную конфигурировать диалект, [используемый при создании Engine](https://github.com/aio-libs/aiopg/blob/master/aiopg/sa/engine.py#L33).

```python
def get_dialect():
  _dialect = PGDialect_psycopg2(json_serializer=json.dumps,
                                json_deserializer=lambda x: x,
                                max_identifier_length=127)

  _dialect.statement_compiler = APGCompiler_psycopg2
  _dialect.implicit_returning = True
  _dialect.supports_native_enum = True
  _dialect.supports_smallserial = True  # 9.2+
  _dialect._backslash_escapes = False
  _dialect.supports_sane_multi_rowcount = True  # psycopg 2.0.9+
  _dialect._has_native_hstore = True

  return _dialect

dialect = get_dialect()
app['db'] = await create_engine(dsn=settings.db_dsn, echo=settings.debug, dialect=dialect)
```

