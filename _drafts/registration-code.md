---
layout: post
title: "Registration Code in PHP"
category: code
---
This code is from:
http://freesourcecodephp.blogspot.com/2011/01/user-login-and-registration-codes-in.html

FREE PHP SOURCE CODES (just copy and paste)

Saturday, January 15, 2011
user login and registration codes in php
Firstly to start with we have to download and install the wamp 
and the lamp server as according to the os we are using,,
then open notepad and start coding (remember to make a dedicated 
folder to avoid ) messing up and loosing the codes,, strictly name the 
programs as instructed or they won't work,
you can yourself edit codes and make changes if you wish to...




This code connects to the database, save this as connect.php and we shall be using this whenever required.

<?php

//ob
ob_start();

//session
session_start();

//connect to database
$error = "Problem connecting";
mysql_connect('server','username','password') or die($error);
mysql_select_db('phpacade_emailactivation') or die($error);

?>








Now what we are going to do is to make a registration page where the users of your website will be able to register themselves by filling the forms,,, you can make changes to the no. of fields and also the field specifications








<?php

include 'connect.php';

if ($_POST['register'])
{
 //get form data
 $username = addslashes(strip_tags($_POST['username']));
 $password = addslashes(strip_tags($_POST['password']));
 $email = addslashes(strip_tags($_POST['email']));
 
 if (!$username||!$password||!$email)
    echo "Please fill out all fields";
 else
 {
    //encrypt password
    $password = md5($password);
    
    //check if username already taken
    $check = mysql_query("SELECT * FROM users WHERE username='$username'");
    if (mysql_num_rows($check)>=1)
       echo "Username already taken";
    else
    {
       //generate random code
       $code = rand(11111111,99999999);
       
       //send activation email
       $to = $email;
       $subject = "Activate your account";
       $headers = "From: alex@phpacademy.info";
       $body = "Hello $username,\n\nYou registered and need to activate your account. Click the link below or paste it into the URL bar of your browser\n\nhttp://phpacademy.info/tutorials/emailactivation/activate.php?code=$code\n\nThanks!";

       if (!mail($to,$subject,$body,$headers))
           echo "We couldn't sign you up at this time. Please try again later.";
       else
       {
           //register into database
           $register = mysql_query("INSERT INTO users VALUES ('','$username','$password','$email','$code','0')");
           echo "You have been registered successfully! Please check your email ($email) to activate your account";
       }

    }
 }
}
else
{

?>

<form action='register.php' method='POST'>
Choose username:<br />
<input type='text' name='username'><p />
Choose password:<br />
<input type='password' name='password'><p />
Email:<br />
<input type='text' name='email'><p />
<input type='submit' name='register' value='Register'>
</form>

<?php

}

?>












Now we have to start coding the login page,here copy and directly paste the code or make any modifications and save it as login.php




<?php

include 'connect.php';

$session_username = $_SESSION['username'];

if ($_POST['login'])
{
   //get form data
   $username = addslashes(strip_tags($_POST['username']));
   $password = addslashes(strip_tags($_POST['password']));
   
   if (!$username||!$password)
      echo "Enter a username and password";
   else
   {
    //log in
    $login = mysql_query("SELECT * FROM users WHERE username='$username'");
    if (mysql_num_rows($login)==0)
       echo "No such user";
    else
    {
      while ($login_row = mysql_fetch_assoc($login))
      {
  
       //get database password
       $password_db = $login_row['password'];
  
       //encrypt form password
       $password = md5($password);
       
       //check password
       if ($password!=$password_db)
          echo "Incorrect password";
       else
       {
          //check if active
          $active = $login_row['active'];
          $email = $login_row['email'];
          
          if ($active==0)
             echo "You haven't activated your account, please check your email ($email)";
          else
          {
           $_SESSION['username']=$username; //assign session
           header("Location: index.php"); //refresh
          }
       }
  
  
      }
    }
   }
}
else
{

  if (isset($session_username))
  {
   echo "You are logged in, $session_username. <a href='logout.php'>Log out</a>";
  }
  else
  {
   echo "
   <form action='index.php' method='POST'>
   Username:

   <input type='text' name='username'><p />
   Password:

   <input type='password' name='password'><p />
   <input type='submit' name='login' value='Log in'>
   </form>
   ";
  }

}

?>

Here this code will be used for the user activation and needs to be saved as activate.php,,,do not make any changes to the source cede here.


<?php

include 'connect.php';

$code = $_GET['code'];

if (!$code)
    echo "No code supplied";
else
{
    $check = mysql_query("SELECT * FROM users WHERE code='$code' AND active='1'");
    if (mysql_num_rows($check)==1)
        echo "You have already activated your account";
    else
    {
        $activate = mysql_query("UPDATE users SET active='1' WHERE code='$code'");
        echo "Your account has been activated!";
    }
    
}
?>



If any of the registered user of your website wants to log out he/she can log out.
The code here has to be saved by the following name logout.php.
<?php

session_start();
session_destroy();

header("Location: index.php");

?>


keep visiting for the new codes
by.
Ankit Kumar
B.Tech
(Electronics and Communicatin Engineering).