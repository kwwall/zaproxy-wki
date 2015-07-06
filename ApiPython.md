# Python client API

The Python client can be downloaded from [SourceForge](http://sourceforge.net/projects/zaproxy/files/client-api/).

It is also available on [PyPI](https://pypi.python.org/pypi/python-owasp-zap-v2) and can be installed using:
```
pip install python-owasp-zap-v2
```

As of ZAP 2.0.0 the Python API is generated (using [this](https://github.com/zaproxy/zaproxy/blob/develop/src/org/zaproxy/zap/extension/api/PythonAPIGenerator.java) class).

Note that the example has now been updated to the v2 API :)


## Building

In order to change/develop ZAP Python API, we need to change the actual code in python/api/src/zapv2/ directory and then run the following commands to build that code and install it system-wide:

```
cd python/api/
python setup.py build
sudo python setup.py install
```

By doing this, we won't be using virtual environment and thus cannot use pip install. By installing the API system-wide, we don't actually need to bother ourselves with pip install. Changes made to the ZAP Python API can be added/committed to repository as normal ZAP code and will eventually be added into the zapv2 egg, which others will be able to install with "pip install zapv2".

For development purposes, changing the API and installing is system-wide is a time saver and works quite nice when we've gotten used to it.


## An example python script
```
#!/usr/bin/env python

import time
from pprint import pprint
from zapv2 import ZAPv2

target = 'http://127.0.0.1'
zap = ZAPv2()
# Use the line below if ZAP is not listening on 8090
# zap = ZAPv2(proxies={'http': 'http://127.0.0.1:8090', 'https': 'http://127.0.0.1:8090'})

# do stuff
print 'Accessing target %s' % target
# try have a unique enough session...
zap.urlopen(target)
# Give the sites tree a chance to get updated
time.sleep(2)

print 'Spidering target %s' % target
zap.spider.scan(target)
# Give the Spider a chance to start
time.sleep(2)
while (int(zap.spider.status) < 100):
    print 'Spider progress %: ' + zap.spider.status
    time.sleep(2)

print 'Spider completed'
# Give the passive scanner a chance to finish
time.sleep(5)

print 'Scanning target %s' % target
zap.ascan.scan(target)
while (int(zap.ascan.status) < 100):
    print 'Scan progress %: ' + zap.ascan.status
    time.sleep(5)

print 'Scan completed'

# Report the results

print 'Hosts: ' + ', '.join(zap.core.hosts)
print 'Alerts: '
pprint (zap.core.alerts())
```

Links:
  * Back: [Maven Plugin](ApiMaven)
  * Home: [The ZAP API](ApiDetails)
  * Next: [API Implementation](ApiImplementation)