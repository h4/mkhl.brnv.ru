# Отправка html-писем питоновским скриптом

```python
template = self._env.get_template(f'{ template_name }.j2')

msg_body = template.render(**data)
msg = MIMEMultipart('alternative')
msg.attach(MIMEText(msg_body, 'html'))

msg['Subject'] = subject
msg['From'] = self._from
msg['To'] = to
if bcc is not None:
  msg['Bcc'] = bcc

s = smtplib.SMTP_SSL(host, port)
s.login(username, password)
s.send_message(msg)
s.quit()
```

