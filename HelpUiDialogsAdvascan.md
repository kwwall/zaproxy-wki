# Active Scan dialog

This dialog launches the [active scanner](HelpStartConceptsAscan).<br>
<h3>Scope</h3>
The first tab allows you to select or change the starting point.<br>If you have more that one <a href='HelpStartConceptsScanpolicy'>scan policies</a> then you will be able to select the one to use.<br>If the starting point is in one or more <a href='HelpStartConceptsContexts'>Contexts</a> then you will be able to choose one of them.<br>If that context has any <a href='HelpStartConceptsUsers'>Users</a> defined then you will be able to select one of them.<br>If you select one of the users then the active scan will be performed as that user, with ZAP (re)authenticating as that user whenever necessary. <br><br>If you select 'recurse' then all of the nodes underneath the one selected will also be scanned.<br>Custom input vectors are only supported if this option is not selected. <br><br>If you select 'Show advanced options' then the following tabs will be shown which provide fine grain control over the active scanning process. <br><br>Clicking on the 'Reset' button will reset all of the options to their default values.<br>
<h3>Input Vectors</h3>
The Input Vectors tab allows you override the default input vectors which are defined in the <a href='HelpUiDialogsOptionsAscaninput'>Options Active Scan Input Vectors screen</a>.<br>Clicking on the 'Reset' button will reset the input vectors to the default options.<br>
<h3>Custom Vectors</h3>
The Custom Vectors tab allows you specify specific locations in the request to attack.<br>Custom Vectors<br>
are only available if the 'recurse' option on the first tab is not selected.<br>To add custom input vectors<br>
highlight the characters you want to attack in the request and lick the 'Add' button.<br>You can add as many<br>
custom input vectors as you want.<br>To remove custom input vectors highlight any of the selected characters<br>
and click the 'Remove' button.<br>Checking the 'Disable non custom input vectors' box disables all of the<br>
input vectors except those you manually define on this tab.<br>
<h3>Technology</h3>
The Technology tab allows you to specify which types of technologies to scan.<br>Un-selecting technologies<br>
that you know are not present in the target application may speed up the scan as rules which target that<br>
technology can skip those tests.<br>
<h3>Policy</h3>
The Policy tab allows you to override any of the settings specified in the selected <a href='HelpStartConceptsScanpolicy'>scan policy</a>. <br><br>
<h2>Accessed via</h2>
<table>
<tr><td></td><td><a href='HelpUiTabsAscan'>Active Scan tab</a></td><td>'New Scan' button</td></tr>
<tr><td></td><td><a href='HelpUiTlmenuTools'>Top level Tools menu</a></td><td>'Active Scan...' menu item</td></tr>
<tr><td></td><td><a href='HelpUiTabsSites'>Sites tab</a></td><td>'Attack / Active Scan... right click menu item</td></tr>
<tr><td></td><td><a href='HelpUiTabsHistory'>History tab</a></td><td>'Attack / Active Scan...' right click menu item</td></tr>
</table>
<h2>See also</h2>
<table>
<tr><td></td><td><a href='HelpUiOverview'>UI Overview</a></td><td>for an overview of the user interface</td></tr>
<tr><td></td><td><a href='HelpUiDialogsDialogs'>Dialogs</a></td><td>for details of the dialogs or popups </td></tr>
</table>