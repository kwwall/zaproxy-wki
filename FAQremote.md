# [FAQ:](FAQtoplevel) How can I connect to ZAP remotely?

By default ZAP will now also only allow connections from the local machine. You can set which IP addresses can connect to the API using the command line:
<pre>-config api.addrs.addr.name=123.456.789.123</pre>
If you are using ZAP in a completely isolated environment you can allow all IP addresses to connect to the ZAP API using:
<pre>-config api.addrs.addr.name=.* -config api.addrs.addr.regex=true</pre>

You will also need to set or disable the API key - see the FAQ: [Why is an API key required by default?](FAQapikey)

If you still have problems connecting then look in the `zap.log` file for any error messages as per the FAQ: [Somethings not working - what should I do?](FAQhelp)

---

[Back to the FAQ](FAQtoplevel)
