mysql.class
===========

###PHP class for work with MySQL database


Connect to database and create object

    require 'mysql.class.php';
    $Query = MySqlClass::connect('localhost','dbname','dbuser','dbpass','utf8');

Simple sql query

    $Query->sql('INSERT INTO tablename VALUES ("value1","value2")');
    ->query() alias of sql()

Get array of first record

    $array = $Query->getarray('SELECT * FROM tablename');
    ->ga() alias of getarray()

Get multiline array of sql query

    $array = $Query->getmultiarray('SELECT * FROM tablename');
    ->gma() is alias of getmultiarray()

Get array values of first field

    $array = $Query->getverticalarray('SELECT * FROM tablename');
    ->gva() is alias of getverticalarray()

Get index array with keys from values first field

    $array = $Query->getindexmultiarray('SELECT * FROM tablename');
    ->gima() is alias of getindexmultiarray()

Get text of last SQL query

    $sqltext = $Query->getLastQuery();

Additional function

    //incoming text is processed using functions: stripslashes, mysql_real_escape_string
    $Query->check_sql($string)
    
    //incoming text is processed using functions: stripslashes, mysql_real_escape_string, htmlspecialchars
    $Query->check_text($string)
    
    Example
    $Query->sql('INSERT INTO tablename VALUES ("'.$Query->check_text($_POST['param1']).'", "'.$Query->check_text($_POST['param2']).'")');
    
    $Query->check_date($date) // example right date 2013-05-15
    $Query->check_time($time) // example right time 13:05:45
    $Query->check_datetime($datetime) // example right datetime 2013-05-15 13:05:45