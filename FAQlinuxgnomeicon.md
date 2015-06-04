# [FAQ:](FAQtoplevel) How can I add an application icon for ZAP to Fedora / Gnome

As root create a file called
  * `/usr/share/applications/owasp-zap.desktop`
containing:
```
[Desktop Entry]
Name=OWASP ZAP
Exec=/opt/owasp/ZAP_1.4.1/zap.sh
Icon=/opt/owasp/ZAP_1.4.1/zap.ico
Categories=Programming;Security;
Type=Application
```
Make sure you correct the paths to match your environment!


---

[Back to the FAQ](FAQtoplevel)