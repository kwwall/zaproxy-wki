# The File menu
This menu handles the current session. By default the following menu items will be present:<br>
<h3>New Session</h3>
This creates a new session.<br>If you have not saved your current session then a warning will be displayed.<br>Starting<br>
a new session without saving the current session will loose all of the data in the current session.<br>
<h3>Open Session...</h3>
This opens a session that has been previously saved.<br>Opening a session without saving the current session<br>
will loose all of the data in the current session.<br>
<h3>Persist Session...</h3>
This persists the current session. <br>While the session is always stored in a database on disk, it will<br>
be lost when ZAP is stopped unless it has been persisted.<br>You only need to persist it once - after that<br>
all changes will be saved.<br>
<h3>Snapshot Session</h3>
This saves a snapshot of a session that has already been persisted.<br>It will use the same filename with<br>
a date-time string appended to it.<br>
<h3>Properties...</h3>
This displays the <a href='HelpUiDialogsSessionSessprop'>Session Properties</a> dialog.<br>This allows you to set the session name and description.<br>
<h3>Load Add-on file...</h3>
Load a local <a href='HelpStartConceptsAddons'>add-on</a> file.<br>Add-ons are typically installed from via the <a href='HelpUiDialogsManageaddons'>Manage Add-ons</a> dialog, but this option can be useful if you have downloaded an add-on manually or are testing one you have developed yourself.<br>Add-ons remain installed until you manually uninstall them.<br>
<h3>Exit and delete session...</h3>
This will exit ZAP and delete the session, even if you have previously persisted it.<br>The session will<br>
no longer be accessible when you restart ZAP, although any snapshots you took will still be available.<br>A<br>
warning dialog will be displayed to ensure you really meant to choose this option.<br>
<h3>Exit</h3>
This will exit ZAP.<br>If you have not saved the current session then you will be given the option to do<br>
so.<br>
<br>
Note that <a href='HelpStartConceptsAddons'>add-ons</a> can add additional menu items.<br>
<h2>See also</h2>
<table>
<tr><td></td><td><a href='HelpUiTlmenuTlmenu'>The top level menu</a></td><td></td></tr>
<tr><td></td><td><a href='HelpUiOverview'>UI Overview</a></td><td>for an overview of the user interface</td></tr>
</table>