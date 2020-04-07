# Замена mp3-тегов на utf-8

```bash
find ./ -iname "*.mp3" -print0 | xargs -0 mid3iconv -eCP1251 --remove-v1 -d
```

