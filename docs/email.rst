Email
=====

Snippets about email.


`Sending-email-with-python`_
----------------------------

I recommend that you use the standard packages email and smtplib together::
    
    # Import smtplib for the actual sending function
    import smtplib

    # Import the email modules we'll need
    from email.mime.text import MIMEText

    # Create a text/plain message
    msg = MIMEText(body)

    # me == the sender's email address
    # you == the recipient's email address
    msg['Subject'] = 'The contents of %s' % textfile
    msg['From'] = me
    msg['To'] = you

    # Send the message via our own SMTP server, but don't include the
    # envelope header.
    s = smtplib.SMTP('localhost')
    s.sendmail(me, [you], msg.as_string())
    s.quit()

For multiple destinations::
    
    # Import smtplib for the actual sending function
    import smtplib

    # Here are the email package modules we'll need
    from email.mime.image import MIMEImage
    from email.mime.multipart import MIMEMultipart

    COMMASPACE = ', '

    # Create the container (outer) email message.
    msg = MIMEMultipart()
    msg['Subject'] = 'Our family reunion'
    # me == the sender's email address
    # family = the list of all recipients' email addresses
    msg['From'] = me
    msg['To'] = COMMASPACE.join(family)
    msg.preamble = 'Our family reunion'

    # Assume we know that the image files are all in PNG format
    for file in pngfiles:
        # Open the files in binary mode.  Let the MIMEImage class automatically
        # guess the specific image type.
        fp = open(file, 'rb')
        img = MIMEImage(fp.read())
        fp.close()
        msg.attach(img)

    # Send the email via our own SMTP server.
    s = smtplib.SMTP('localhost')
    s.sendmail(me, family, msg.as_string())
    s.quit()


`Sending mail via sendmail from python`_
----------------------------------------

If I want to send mail not via SMTP, but rather via sendmail::
    
    from email.mime.text import MIMEText
    from subprocess import Popen, PIPE

    msg = MIMEText("Here is the body of my message")
    msg["From"] = "me@example.com"
    msg["To"] = "you@example.com"
    msg["Subject"] = "This is the subject."
    p = Popen(["/usr/sbin/sendmail", "-t"], stdin=PIPE)
    p.communicate(msg.as_string())


.. _Sending-email-with-python: http://stackoverflow.com/questions/6270782/sending-email-with-python
.. _Sending mail via sendmail from python: http://stackoverflow.com/questions/73781/sending-mail-via-sendmail-from-python
