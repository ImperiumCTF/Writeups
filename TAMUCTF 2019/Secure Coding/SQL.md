## SQL - Secure Coding

**Challenge:** : [https://gitlab.tamuctf.com/root/sql](https://gitlab.tamuctf.com/root/sql)
**Difficulty:**: easy
**Solved by:** Neolex  

**Solution:**  
The goal of this challenge is to secure the vulnerable script of the web challenge "Not Another SQLi Challenge" . 
Here is the vulnerable script :  
```php
<?php
  ini_set('display_errors', 'On');
  error_reporting(E_ALL | E_STRICT);
  echo "<html>";
  if (isset($_POST["username"]) && isset($_POST["password"])) {
    $servername = "localhost";
    $username = "sqli-user";
    $password = 'AxU3a9w-azMC7LKzxrVJ^tu5qnM_98Eb';
    $dbname = "SqliDB";
    $conn = new mysqli($servername, $username, $password, $dbname);
    if ($conn->connect_error)
        die("Connection failed: " . $conn->connect_error);
    $user = $_POST['username'];
    $pass = $_POST['password'];
    $sql = "SELECT * FROM login WHERE User='$user' AND Password='$pass'";
    if ($result = $conn->query($sql))
    {
      if ($result->num_rows >= 1)
      {
        $row = $result->fetch_assoc(); 
        echo "You logged in as " . $row["User"];
        $row = $result->fetch_assoc();
        echo "<html>You logged in as " . $row["User"] . "</html>\n";
      }
      else {
        echo "Sorry to say, that's invalid login info!";
      }
    }
    $conn->close();
  }
  else
    echo "Must supply username and password...";
  echo "</html>";
?>
```

Here is the diff with the secured code : 
```diff
13,14c13,14
<     $user = $_POST['username'];
<     $pass = $_POST['password'];
---
>     $user = mysqli_real_escape_string($conn, $_POST['username']);
>     $pass = mysqli_real_escape_string($conn,$_POST['password']);
```

**Flag:**  
gigem{the_best_damn_sql_anywhere}

