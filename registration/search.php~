<html>
<head>
<Title>Search</Title>
<style type="text/css">
    body { background-color: #fff; border-top: solid 10px #000;
        color: #333; font-size: .85em; margin: 20; padding: 20;
        font-family: "Segoe UI", Verdana, Helvetica, Sans-Serif;
    }
    h1, h2, h3,{ color: #000; margin-bottom: 0; padding-bottom: 0; }
    h1 { font-size: 2em; }
    h2 { font-size: 1.75em; }
    h3 { font-size: 1.2em; }
    table { margin-top: 0.75em; }
    th { font-size: 1.2em; text-align: left; border: none; padding-left: 0; }
    td { padding: 0.25em 2em 0.25em 0em; border: 0 none; }
</style>
</head>
<body>
<h1>Search here!</h1>
<p>Enter your query</p>
<form method="post" action="search.php" enctype="multipart/form-data" >
      Query  <input type="text" name="query" id="query"/></br>
      <input type="submit" name="submit" value="Submit" />
</form>
<?php
    // DB connection info
    //TODO: Update the values for $host, $user, $pwd, and $db
    //using the values you retrieved earlier from the portal.
    $host = "eu-cdbr-azure-west-b.cloudapp.net";
    $user = "bfd65bd6b43768";
    $pwd = "173bccdb";
    $db = "gmcours";
    // Connect to database.
    try {
        $conn = new PDO( "mysql:host=$host;dbname=$db", $user, $pwd);
        $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
    }
    catch(Exception $e){
        die(var_dump($e));
    }
    // Insert registration info
    if(!empty($_POST)) {
    try {
        $query = $_POST['query'];
	$display = FALSE;
	if(substr_count($query, "COUNT") > 0) 
	{
		$display = TRUE;
		$query = str_replace("COUNT(*)", "*", $query);
		
	}

        
        $stmt = $conn->query($query);
 	$registrants = $stmt->fetchAll(); 
        echo "<h2>Search result :</h2>";
	if($display)
	{
		echo "Count : ".count($registrants);
	}
	else{
        echo "<table>";
        echo "<tr><th>Name</th>";
	echo "<th>Company</th>";
        echo "<th>Email</th>";
        echo "<th>Date</th></tr>";
        foreach($registrants as $registrant) {
            echo "<tr><td>".$registrant['name']."</td>";
            echo "<td>".$registrant['Company']."</td>";
            echo "<td>".$registrant['email']."</td>";
            echo "<td>".$registrant['date']."</td></tr>";
        }
        echo "</table>";
   	 }
    }
    catch(Exception $e) {
        die(var_dump($e));
    }
  }
?>
</body>
</html>
