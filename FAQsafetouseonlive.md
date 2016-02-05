# [FAQ:](FAQtoplevel)  Is there any danger when scanning with ZAP against a live website (e.g. create/delete/update/corrupt data)?

Proxying (and therefore passive scanning) requests via ZAP is completely safe and legal, it just allows you to see whats going on.

Spidering is a bit more dangerous. It could cause problems depending on how your application works.

Note that there is an Spider option to not use POST requests - this may be safer but is also likely to reduce the effectiveness of the Spider.

Active scanning is dangerous and depending on your app may create/modify/delete data.

So the only really safe thing is proxying and passive scanning, the other 2 could cause problems and could be considered illegal if you perform them on apps you dont have permission to test.

ZAP supports a 'safe' [mode](https://github.com/psiinon/zap-wiki-test/wiki/HelpStartConceptsModes) which will only allow you to do safe things, as well as a 'protected' mode which only allows you to attack sites that you define are in [scope](https://github.com/psiinon/zap-wiki-test/wiki/HelpStartConceptsScope). We recommend you use either of these modes whenever you are using ZAP with a site that you do not want to attack.