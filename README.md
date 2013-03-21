JavaMail for Android
================

Javamail 1.4.7 for Android with SASL authentication support.

This is a JavaMail fork for Android with proper SASL authentication support. 
It was made to work with this example: 
https://code.google.com/p/google-mail-oauth2-tools/wiki/JavaSampleCode

Known Issues:
-----

Currently, there are issues with Mailcap so javamail cannot find a correct handler for multipart messages.

The current workaround is to have this piece of code before any Javamail code.

```java
MailcapCommandMap mc = (MailcapCommandMap) CommandMap.getDefaultCommandMap();
mc.addMailcap("text/html;; x-java-content-handler=com.sun.mail.handlers.text_html");
mc.addMailcap("text/xml;; x-java-content-handler=com.sun.mail.handlers.text_xml");
mc.addMailcap("text/plain;; x-java-content-handler=com.sun.mail.handlers.text_plain");
mc.addMailcap("multipart/*;; x-java-content-handler=com.sun.mail.handlers.multipart_mixed");
mc.addMailcap("image/gif;;	x-java-content-handler=com.sun.mail.handlers.image_gif");
mc.addMailcap("image/jpeg;;	x-java-content-handler=com.sun.mail.handlers.image_jpeg");
mc.addMailcap("image/png;;	x-java-content-handler=com.sun.mail.handlers.image_png");
CommandMap.setDefaultCommandMap(mc);
```

License
-----

This project follows the original licensing of JavaMail.

As stated [here][1]:

	JavaMail uses several licenses:
	Most of the JavaMail source code is licensed under the CDDL license
	and the GPLv2 with Classpath Exception license; see the license information
	at the top of each source file.

[1]: http://kenai.com/projects/javamail/pages/License
