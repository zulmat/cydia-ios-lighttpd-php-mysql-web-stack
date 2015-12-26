08/2015<br>
<br>
<br>
<br>
<h1>This package is obsolete!</h1>

<br>
<h1>Introduction</h1>
<h2>Note</h2>

<b>This package is just a prov of concept!</b> It combines the already existing cydia packages 'lighttpd', 'png', 'jpeg', 'tiff' (by Saurik) and 'mysql' (by BigBoss/Wizardry and Steamworks) with my new package 'PHP53'.<br>
Due to vulnerability <b>I can not recommend to install these packages</b> without install my newer packages 'lighttpd-atv', 'PHP54', 'OpenSSL' 'libpng','libjpeg' and 'libtiff' !<br>
<br>
<b>Do not install this package on an AppleTV2 device.</b><br>
Instead of this, use the cydia package <a href='AtvLighttpdPhpMysql.md'>atv-lighttpd-php-mysql</a>.<br>
<br>
<b>Please SSH in your iOS device and change the passwords for the user 'root' and 'mobile'. Hacker will know them very well.</b><br>
Cydia will show you how that works. Or view this [<a href='http://www.youtube.com/watch?v=vQdCrCzPOL0'>video</a>]<br>
<br>
<br>
<h1>The Package</h1>
The cydia package <b>touch-lighttpd-php-mysql</b> will also install:<br>
<ul><li>the webserver <b>Lighttpd</b> (cydia package ID: lighttpd)<br>
</li><li><b>PHP 5.3.28</b> (cydia package ID: php53)<br>
</li><li>the database server <b>MySQL</b>(cydia package ID: com.was.mysql)<br>
</li><li>the packages OpenSSL (cydia package ID: openssl)<br>
</li><li>the packages libjpeg (cydia package ID: jpeg)<br>
</li><li>the packages libpng (cydia package ID: png)<br>
</li><li>the packages libtiff (cydia package ID: tiff)<br>
</li><li>and some packages for the daemon launcher</li></ul>

<b>Due to vulnerability, please be careful with it. Saurik's Lighttpd, OpenSSL, libjpeg, libpng and libtiff are not up do date!</b>

With this composition you get a full web stack to host your own content.<br>

The used <b>PHP 5.3.x</b> supports fast-cgi, pdo_mysql, mysql, mysqli, mysqlnd, pdo_sqlite, sqlite3, pdo_pgsql, pgsql, gd (gif, png, bmp, xbm, tiff, jpeg and FreeType2), mbstring, exif, dom, xml2, xmlreader, xmlwriter, xslt, json, pcre, phar, calendar, reflection, session, zlib, zip, bz2, mcrypt, openssl, soap, sockets, ftp, pcntl.<br>
<br>
<br>
<h1>Add Cydia Repo Source</h1>
You will find the project package here:<br>
<b><a href='http://ios-webstack.tk/cydia'>http://ios-webstack.tk/cydia</a></b>

You can add it in Cydia, NitoTV or direct with following command:<br>
<pre><code>echo 'deb http://ios-webstack.tk/cydia/ ./' &gt; /etc/apt/sources.list.d/ios-webstack.list<br>
</code></pre>
For your security I advice you to add the PGP public key of the iOS WebStack Cydia repo. (<a href='http://www.ios-webstack.tk/public-key'>How to</a>)<br>
<br>
<br>
<h1>Installation</h1>
Please use Cydia or the command 'apt-get install touch-lighttpd-php-mysql'.<br>
The MySQL root user password is not set during the installation.<br>
<br>
<b>Due to vulnerability, please be careful with this package. Sauriks Lighttpd, Libjpeg, Libpng and Libtiff are not up do date!</b>

<br>
<h1>Setup MySQL</h1>
After the installation you have to do two steps<br>
<ul><li><b>clean up your MySQL database</b>
</li><li><b>set a fresh MySQL root user password</b></li></ul>

The also installed PHP-Script <a href='http://www.adminer.org'>Adminer</a> will help you to do that.<br>
<br>
If you open Safari on your iOS device and if you then load the following site <a href='http://localhost'>http://localhost</a> , you will get all necessary information.<br>
<br>
<b>Please do it as described. Otherwise, hacker will love your device.</b>

<br>
<h1>Your Web Content</h1>
Now you can place your web content in <b>/var/www</b> or you can install cydia packages like:<br>
<ul><li>ownCloud-atv<br>
</li><li>websitepaker-atv<br>
</li><li>wordpress-atv<br>
</li><li>phpmyadmin-atv<br>
</li><li>etc.</li></ul>

<br>
<h1>Enable/Disable Services</h1>
To save your battery power and for safety reasons you can switch the web services on and off.<br>
You will find in your iOS device Extention Settings two icons called 'Lighttpd' and 'MySQL'.<br>
<br>
If you would like restart the services , please wait 10 second between off and on switching.<br>
<br>
<b>If you not need the services, please disable these. Otherwise hacker will love your device.</b>

<br>
<h1>Log Files</h1>
<ul><li><b>Lighttpd</b> log files are stored in /var/log/lighttpd (disabled) (the owner of the Lighttpd log folder must be <code>daemon:_www</code> )<br>
</li><li><b>PHP</b> log files are stored in /var/log/lighttpd (disabled).<br>
</li><li><b>MySQL</b> logfiles are stored in /var/log</li></ul>

<br>
<h1>Configuration Files</h1>
<h2>Lighttpd Configuration</h2>
The packages include configuration files for Lighttpd in <b>/etc/lighttpd/</b><br>
Hint: Because Sauriks older Lighttpd is used within this packages, I have to established the old config file structure for it. Therefore there is a symlink from /etc/lighttpd.conf to /etc/lighttpd/lighttpd-atv.conf.<br>
<br>
<b>File: /etc/lighttpd/lighttpd-atv.conf</b>
<pre><code># Cydia Package touch-lighttpd-php-mysql<br>
#<br>
# This is an 'EXAMPLE' configuration file for Lighttpd. <br>
# The configuration is prepared for PHP fastcgi support.<br>
# It is up to you to change it.<br>
# If you need more information please have a look at following page:<br>
# http://redmine.lighttpd.net/projects/lighttpd/wiki/Docs<br>
<br>
include "lighttpd/mod_fastcgi.conf"<br>
<br>
server.document-root           = "/var/www/"<br>
server.port                    = 80<br>
<br>
<br>
#If it is possible, please do not change values inside this block:<br>
#[BEGIN] ---- be careful ----<br>
<br>
#If you would like change the Server-Username<br>
#then you have to change the log folder permission<br>
#-&gt; chown -R 'Server-Username':'Server-Groupname' lighttpd<br>
server.username                = "daemon"<br>
server.groupname               = "_www"<br>
#server.errorlog                = "/var/log/lighttpd/lighttpd.err"  #No error logging on iPad/iPhone <br>
#accesslog.filename             = "/var/log/lighttpd/lighttpd.log"  #No access logging on iPad/iPhone<br>
server.pid-file                = "/var/run/lighttpd.pid"<br>
#[END] ---- be careful ----<br>
<br>
server.modules                 = (<br>
            "mod_access",<br>
#            "mod_accesslog",      #No access logging on iPad/iPhone<br>
            "mod_fastcgi",<br>
            "mod_cgi",<br>
            "mod_compress",<br>
            "mod_evasive",<br>
            "mod_rewrite"         <br>
)<br>
<br>
static-file.exclude-extensions = ( ".fcgi", ".php", ".rb", ".pl", ".cgi", ".inc" )<br>
url.access-deny                = ( "~", ".sqlite")<br>
evasive.max-conns-per-ip       = 10<br>
compress.cache-dir             = "/tmp/"<br>
compress.filetype              = ("text/plain", "text/html")<br>
server.max-fds                 = 256<br>
<br>
#Don't place important server information in server.tag . Hacker will check them first.<br>
#Try curl -I http://your.iOS-Web.server to see what lighttpd get<br>
server.tag                     = ""<br>
#server.name                   = "www.add_your_servername.com"<br>
#server.max-connections        = 10<br>
#server.error-handler-404      = "404error.html"<br>
#server.kbytes-per-second      = 120<br>
#connection.kbytes-per-second  = 32<br>
<br>
index-file.names = ("index.html", "index.php", "index.htm")<br>
<br>
mimetype.assign             = (<br>
  ".pdf"          =&gt;      "application/pdf",<br>
  ".sig"          =&gt;      "application/pgp-signature",<br>
  ".spl"          =&gt;      "application/futuresplash",<br>
  ".class"        =&gt;      "application/octet-stream",<br>
  ".ps"           =&gt;      "application/postscript",<br>
  ".torrent"      =&gt;      "application/x-bittorrent",<br>
  ".dvi"          =&gt;      "application/x-dvi",<br>
  ".gz"           =&gt;      "application/x-gzip",<br>
  ".pac"          =&gt;      "application/x-ns-proxy-autoconfig",<br>
  ".swf"          =&gt;      "application/x-shockwave-flash",<br>
  ".tar.gz"       =&gt;      "application/x-tgz",<br>
  ".tgz"          =&gt;      "application/x-tgz",<br>
  ".tar"          =&gt;      "application/x-tar",<br>
  ".zip"          =&gt;      "application/zip",<br>
  ".mp3"          =&gt;      "audio/mpeg",<br>
  ".m3u"          =&gt;      "audio/x-mpegurl",<br>
  ".wma"          =&gt;      "audio/x-ms-wma",<br>
  ".wax"          =&gt;      "audio/x-ms-wax",<br>
  ".ogg"          =&gt;      "audio/x-wav",<br>
  ".wav"          =&gt;      "audio/x-wav",<br>
  ".gif"          =&gt;      "image/gif",<br>
  ".jpg"          =&gt;      "image/jpeg",<br>
  ".jpeg"         =&gt;      "image/jpeg",<br>
  ".png"          =&gt;      "image/png",<br>
  ".svg"          =&gt;      "image/svg+xml",<br>
  ".xbm"          =&gt;      "image/x-xbitmap",<br>
  ".xpm"          =&gt;      "image/x-xpixmap",<br>
  ".xwd"          =&gt;      "image/x-xwindowdump",<br>
  ".css"          =&gt;      "text/css",<br>
  ".html"         =&gt;      "text/html",<br>
  ".htm"          =&gt;      "text/html",<br>
  ".js"           =&gt;      "text/javascript",<br>
  ".asc"          =&gt;      "text/plain",<br>
  ".c"            =&gt;      "text/plain",<br>
  ".conf"         =&gt;      "text/plain",<br>
  ".text"         =&gt;      "text/plain",<br>
  ".txt"          =&gt;      "text/plain",<br>
  ".dtd"          =&gt;      "text/xml",<br>
  ".xml"          =&gt;      "text/xml",<br>
  ".mpeg"         =&gt;      "video/mpeg",<br>
  ".mpg"          =&gt;      "video/mpeg",<br>
  ".mov"          =&gt;      "video/quicktime",<br>
  ".qt"           =&gt;      "video/quicktime",<br>
  ".avi"          =&gt;      "video/x-msvideo",<br>
  ".asf"          =&gt;      "video/x-ms-asf",<br>
  ".asx"          =&gt;      "video/x-ms-asf",<br>
  ".wmv"          =&gt;      "video/x-ms-wmv",<br>
  ".bz2"          =&gt;      "application/x-bzip",<br>
  ".tbz"          =&gt;      "application/x-bzip-compressed-tar",<br>
  ".tar.bz2"      =&gt;      "application/x-bzip-compressed-tar"<br>
)<br>
</code></pre>

<br>
<b>File: /etc/lighttpd/mod_fast-cgi-atv.conf</b>
<pre><code>fastcgi.server = ( ".php" =&gt;<br>
  ( "localhost" =&gt;<br>
     (<br>
     "bin-path" =&gt; "/usr/local/bin/php-cgi",<br>
     "socket" =&gt; "/tmp/php.socket",<br>
     "max-procs" =&gt; 1,<br>
     "bin-environment" =&gt; <br>
        (<br>
        "PHP_FCGI_CHILDREN" =&gt; "2"<br>
        )<br>
     )<br>
  )<br>
)<br>
</code></pre>

<br>
<h2>PHP Configuration</h2>
The packages include configuration files for PHP in <b>/etc/</b> and extension configuration files in <b>/etc/php.d/</b><br>
Hint: The default configured time zone is <b>date.timezone="UTC"</b>.<br>
<br>
<b>File: /etc/php.ini</b>
<pre><code>; PHP Example Configuration of Cydia packages iOS-WebStack<br>
<br>
;This is an 'EXAMPLE' configuration file for PHP.<br>
<br>
;Be careful with the socket path<br>
mysql.default_socket     = /tmp/mysql.sock<br>
pdo_mysql.default_socket = /tmp/mysql.sock<br>
mysqli.default_socket    = /tmp/mysql.sock<br>
<br>
;Limits<br>
upload_max_filesize = 10M<br>
post_max_size = 10M<br>
<br>
;TimeZone<br>
;You should simply replace "Europe/Berlin" with the desired timezone.<br>
;The full list of supported time zones is available here: http://www.php.net/manual/en/timezones.php<br>
date.timezone = "Europe/Berlin"<br>
<br>
<br>
<br>
;I recommends to place following lines to /etc/php.d/security.ini (it will not be touched<br>
;from a cydia packages update).<br>
;========================================================================================<br>
<br>
;Please have a look at http://www.cyberciti.biz/tips/php-security-best-practices-tutorial.html<br>
;It is up to you to comment-out some directives.<br>
<br>
;Make sure you log all php errors to a log file.<br>
;Make sure that php and lighttpd have write permissions.<br>
log_errors=Off<br>
error_log=/var/log/lighttpd/php_scripts_error.log<br>
<br>
;To restrict PHP information leakage disable expose_php.<br>
;Have a check befor and after: curl -I http://your.iOS-Web.server/yourPHPsite.php<br>
 expose_php=Off<br>
<br>
;Do not expose PHP error messages to all site visitors.<br>
; display_errors=Off<br>
<br>
;The allow_url_fopen option allows PHP's file functions - such as file_get_contents() and the<br>
;include and require statements - can retrieve data from remote locations using ftp or http<br>
;protocols. Programmers frequently forget this and don't do proper input filtering when passing<br>
;user-provided data to these functions, opening them up to code injection vulnerabilities.<br>
;A large number of code injection vulnerabilities reported in PHP-based web applications are<br>
;caused by the combination of enabling allow_url_fopen and bad input filtering.<br>
; allow_url_fopen=Off<br>
<br>
;I also recommend to disable allow_url_include for security reasons:<br>
; allow_url_include=Off<br>
<br>
;If turned On, mysql_connect() and mysql_pconnect() ignore any arguments passed to them.<br>
;Please note that you may have to make some changes to your code. Third party and open source<br>
;application such as WordPress, and others may not work at all when sql.safe_mode enabled.<br>
; sql.safe_mode=On<br>
<br>
;It is also recommended that you turn off magic_quotes_gpc for all php 5.3.x installations<br>
;as the filtering by it is ineffective and not very robust. mysql_escape_string() and<br>
;custom filtering functions serve a better purpose (hat tip to Eric Hansen):<br>
; magic_quotes_gpc=Off<br>
<br>
;You can set maximum execution time of each php script, in seconds.<br>
;Another recommend option is to set maximum amount of time each script<br>
;may spend parsing request data, and maximum amount of memory a script may consume.<br>
;GD picture converting needs a lot of memory. Be carefull with 'memory_limit'<br>
;Set in seconds:<br>
; max_execution_time =  30<br>
; max_input_time = 30<br>
; memory_limit = 40M<br>
</code></pre>
<br>
<b>File: /etc/php.d/php.ini</b>
<pre><code>;You can splite this file in separate INI files.<br>
;If you do that, please remember the extension loading<br>
;order of INI files (alphabetically).<br>
<br>
extension=iconv.so<br>
<br>
extension=mbstring.so<br>
<br>
extension=curl.so<br>
<br>
;The loading order is important<br>
extension=sqlite3.so<br>
extension=pdo_sqlite.so<br>
<br>
;The loading order is important<br>
extension=mysqlnd.so<br>
extension=mysqli.so<br>
extension=mysql.so<br>
extension=pdo_mysql.so<br>
<br>
;The loading order is important<br>
;extension=pgsql.so<br>
;extension=pdo_pgsql.so<br>
<br>
;Must be loaded after mbstring.so<br>
extension=exif.so<br>
<br>
extension=gd.so<br>
<br>
extension=zip.so<br>
<br>
extension=bz2.so<br>
<br>
extension=calendar.so <br>
<br>
extension=xsl.so<br>
<br>
extension=openssl.so<br>
<br>
extension=ftp.so<br>
<br>
extension=sockets.so<br>
<br>
extension=pcntl.so<br>
</code></pre>

<br>
<h2>MySQL Configuration</h2>
The packages does not include configuration files for MySQL.<br>
See <a href='http://was.fm/ios:mysql'>http://was.fm/ios:mysql</a>

<br>
<h1>Finish</h1>
If you don't need the package main sites /var/www/index.php and /var/www/adminer.php, feel free to delete them.