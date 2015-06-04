# BeanShell Console dialog
### Introduction / What is the BeanShell

The [BeanShell](http://www.beanshell.org/) is an interactive Java shell that can be used to execute BeanShell scripts. These scripts are a simplified form of Java that use many elements from Java syntax, but in a simpler scripting format. All Java code is also valid BeanShell code. BeanShell integration in OWASP ZAP enables you to write scripts using the ZAP functions and data set. This can be a very powerful feature for analyzing web applications.
### BeanShell Console

The console is started from the Tools menu, and contains a split screen where the top half is the interactive
BeanShell console and the bottom half is a simple text editor. For complex scripts, you're encouraged
to use a Java editor. Scripts can be loaded, saved and evaluated from the editor.

When the BeanShell starts a number of objects from ZAP are available for use, namely:
  * the _Model_ singleton, through the object named **_model_**
  * the _SiteTree_ tree of current sites through the **_sites_** object
  * an instance of _HttpSender_ through the **_sender_** object

Notice that the BeanShell is loosely typed. Therefore, it is not necessary to declare variables before
using them – this makes scripts a bit more concise than regular Java. But of course, if you did want
to define the type you can.
### Using the Site Map

Let's start with something useful and typical: Iterate through all the site nodes and check for the existence
of a file. A script has already been created that accomplishes this, choose _Load_ and select the _example.tree.bsh_
file.
<pre>
import org.apache.commons.httpclient.URI;<br>
import org.parosproxy.paros.network.HttpMessage;<br>
import org.parosproxy.paros.model.*;<br>
<br>
Tree () {<br>
<br>
find (SiteNode node, String resource) {<br>
if (node == null) return;<br>
ref = node.getHistoryReference();<br>
if ((ref != null) && (!node.isLeaf())) {<br>
checkExists(ref, resource);<br>
}<br>
for (i=0;i<node.getChildCount();i++) {<br>
try {<br>
find (node.getChildAt(i), resource);<br>
} catch (Exception e) {<br>
e.printStackTrace();<br>
}<br>
}<br>
}<br>
<br>
checkExists(ref, resource) {<br>
u = ref.getHttpMessage().getRequestHeader().getURI().toString() + "/" + resource;<br>
msg = ref.getHttpMessage();<br>
msg.getRequestHeader().setURI(new URI(u));<br>
sender.sendAndReceive(msg, true);<br>
if (msg.getResponseHeader().getStatusCode() == 200) {<br>
print("Found: "+msg.getRequestHeader().getURI().toString());<br>
}<br>
}<br>
<br>
return this;<br>
}<br>
</pre>

Before clicking Evaluate, first browse to a site through ZAP to populate the tree:

Now click on evaluate to execute the script that's in the editor. If there are no errors, then you can
now start using the object defined in the script by issuing these commands:
<pre>
t = Tree();<br>
</pre>

This constructs a new Tree object and assigns a reference to _t_.
<pre>
t.find(sites.getRoot(), "index.html");<br>
</pre>

Call the _find_ method on t, which takes a _SiteNode_ as the first argument and a resource to find as the
second. In this case, the method will iterate through all the nodes in the tree, because we started at
the root, and will find index.html files.

Instead of iterating through all the nodes, we could also choose to start a specific node by using the
_findChild_ method.

This should give you some idea of the power of the BeanShell in ZAP. But to fully exploit it, you'll
need to familiarize yourself with the internal API and the BeanShell's features. The BeanShell has been
setup so as to allow full access to all internal objects and methods – even private ones.
### Simple HTTP Request

In the next example, we create and send an HTTP request directly in the interactive console:
<pre>
TBD<br>
</pre>

To fully utilize the power of the BeanShell, you should familiarize yourself with ZAP's internals. The
_sender_ object is the same instance as is used by the [Manual Request Editor](HelpUiDialogsMan_req) and will therefore automatically use proxy settings set in the ZAP configuration.
<pre>
TBD<br>
</pre>
### Tips

Use the _unset(String)_ command to unset any declared variables, methods or objects. This is useful if
you want to replace a method declaration in the current namespace. Note that the command takes a String
argument, not an Object, so to unset the _t_ object we used above, it should be: _unset("t");_ and not _unset(t);_

## Accessed via
<table>
<tr><td></td><td><a href='HelpUiTlmenuTools'>Top level Tools menu</a></td><td>'BeanShell Console' menu item</td></tr>
</table>
## See also
<table>
<tr><td></td><td><a href='HelpUiOverview'>UI Overview</a></td><td>for an overview of the user interface</td></tr>
<tr><td></td><td><a href='HelpUiDialogsDialogs'>Dialogs</a></td><td>for details of the dialogs or popups </td></tr>
</table>