# Release 1.1.0

The following changes were made in this release:
## Significant changes:
### OWASP rebranding
ZAP has been accepted as an OWASP project.<br>Its homepage is now: <a href='http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project'>http://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project</a>
<h3>Brute Force</h3>
The ability to brute force files and directories based on code from the OWASP DirBuster project. <br>The<br>
new Brute Force tab shows the files and directories found.<br>
<h3>Port Scan</h3>
The ability to port scan sites. <br>The new Port Scan tab shows the ports found.<br>
<h3>Active Scan tab</h3>
The new <a href='HelpUiTabsAscan'>Active Scan tab</a> shows the requests and responses as a result of actively scanning a site.<br>
<h3>Spider tab</h3>
The <a href='HelpUiTabsSpider'>Spider tab</a> now allows you to continue using ZAP while spidering a site.<br>You can also pause and resume the spider.<br>
<h3>Smartcard support</h3>
Smart card support has been added c/o the Andiparos project.<br>The following smartcard devices have been<br>
tested on Windows:<br>
<table>
<tr><td></td><td>Safeguard</td><td>Aladdin eToken</td></tr>
<tr><td></td><td></td><td>Aladdin eToken Pro</td></tr>
<tr><td></td><td>Omnikey</td><td>Omnikey 3121</td></tr>
<tr><td></td><td></td><td>CardMan 6121</td></tr>
<tr><td></td><td>Gemalto</td><td>Reflex 20 V2</td></tr>
<tr><td></td><td></td><td>Swiss Stick</td></tr>
</table>
The following smartcard devices are reported to work:<br>
<table>
<tr><td></td><td>Omnikey</td><td>CardMan 4040</td></tr>
</table>
<h3>Attack menu</h3>
The new <a href='HelpUiTabsSites'>Sites tab</a> right click 'Attack' menu allows you to start various scans.<br>
<h3>More internationalisation</h3>
All of the main tabs and menu items have now been internationalised.<br>
<h3>Localisation</h3>
Support for the following languages are built into this version:<br>
<table>
<tr><td></td><td>English</td><td>The default language</td></tr>
<tr><td></td><td>Brazilian Portuguese</td><td></td></tr>
<tr><td></td><td>German</td><td></td></tr>
<tr><td></td><td>Polish</td><td></td></tr>
<tr><td></td><td>Spanish</td><td></td></tr>
</table>
<h3>Language selection</h3>
On start up you will be prompted to choose the language to use.<br>New languages are automatically detected<br>
by the presence of files with names of the form Messages<code>_</code><code>&lt;</code>locale<code>&gt;</code>.properties in the ZAP directory.<br>
<h2>Minor changes:</h2>
<h3>Disabled 'default file' plugins</h3>
The plugins which detect default files are effectively made redundant by the new brute force scanner.<br>These<br>
have therefore been disabled.<br>
<h3>Scanner summaries</h3>
Counts of the number and types of the current scans are now displayed in the <a href='HelpUiFooter'>footer</a>.<br>
<h2>See also</h2>
<table>
<tr><td></td><td><a href='HelpIntro'>Introduction</a></td><td>the introduction to ZAP</td></tr>
<tr><td></td><td><a href='HelpReleasesReleases'>Releases</a></td><td>the full set of releases</td></tr>
<tr><td></td><td><a href='HelpCredits'>Credits</a></td><td>the people and groups who have made this release possible</td></tr>
</table>