Email
=====

Snippets about email.


Sending mail via sendmail from python
-------------------------------------

If I want to send mail not via SMTP, but rather via sendmail::
    
    from email.mime.text import MIMEText
    from subprocess import Popen, PIPE

    msg = MIMEText("Here is the body of my message")
    msg["From"] = "me@example.com"
    msg["To"] = "you@example.com"
    msg["Subject"] = "This is the subject."
    p = Popen(["/usr/sbin/sendmail", "-t"], stdin=PIPE)
    p.communicate(msg.as_string())
