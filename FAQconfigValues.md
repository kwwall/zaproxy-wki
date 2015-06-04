# How do you find out what key to use to set a config value on the command line?

The ZAP command line allows you to set individual values as follows:
```
-config api.key=12345 -config connection.timeoutInSecs=60
```
How can you find out what keys to use to set the values you want?

The keys are a dot notation of the XML used in the config.xml file.

One way to find out which value you need to change is:
  1. Start ZAP with a clean directory, eg
    * ./zap.sh -dir test1
  1. Close ZAP
  1. Start ZAP with another clean directory, eg
    * ./zap.sh -dir test2
  1. Set the option you want to know the key of
  1. Close ZAP
  1. Diff the 2 config files:
    * diff test1/config.xml test2/config.xml
  1. Work out the XML hierarchy of the item that has changed
  1. Convert that to dot notation

For example, the default scanner strength level is in:
```
<scanner><strength>MEDIUM</strength></scanner>
```
Which in dot notation is:
```
scanner.strength=MEDIUM
```


---

[Back to the FAQ](FAQtoplevel)