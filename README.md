<?php
$insert=false;

if(isset($_POST['name'])){
    
    $server="localhost";
    $username="root";
    $password="";
    $database="trip"; 
    
    $con=new mysqli($server,$username,$password, $database);
    
    if($con->connect_error)
    {
        die("Couldn't connect: " . $con->connect_error);
    
    }
    
    
    $name=$_POST['name'];
    $age=$_POST['age'];
    $gender=$_POST['gender'];
    $email=$_POST['email'];
    $phone=$_POST['phone'];
    $desc=$_POST['desc'];
    
    $sql="INSERT INTO `trip` (`name`, `age`, `gender`, `email`, `phone`, `other`, `date`)
    VALUES ('$name', '$age', '$gender', '$email', '$phone', '$desc', current_timestamp());";
    
    if($con->query($sql)==TRUE){
        $insert=true;
    }
    else{
        echo "ERROR: $sql <br> " . $con->error;
    }
    $con->close();
}



?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to Travel form</title>
    <link rel="stylesheet" href="Style.css">
</head>
<body>
    <img class="bg" src="Travel-HD-Wallpaper-Free-download.jpg" alt="SASTRA">
    <div class="container">
        <h1>Welcome to SASTRA University</h1>
        <p>Enter your details to confirm your participation in the trip</p> 
        <?php
            if($insert == true){
                echo "<p class='submitMsg'>Thanks for submitting your form. We are happy to see you joining us for the US trip.</p>";
            }
        ?>
        <form action="index.php" method="post">
            <input type="text" name="name" id="name" placeholder="Enter your name">   
            <input type="text" name="age" id="age" placeholder="Enter your age"> 
            <input type="text" name="gender" id="gender" placeholder="Enter your gender">
            <input type="email" name="email" id="email" placeholder="Enter Your email">
            <input type="text" name="phone" id="phone" placeholder="Enter your phone number"> 
            <textarea name="desc" id="desc" cols="30" rows="10" placeholder="Enter Other information here"></textarea>
            <button class="btn" type="submit">Submit</button>
        </form>
    </div>

    <script src="index.js"></script>


    <style>*{
    margin:0px;
    padding: 0px;
    box-sizing: border-box;
}
.container{
    max-width:80%;
  /*  background-color: rgb(171, 142, 199);*/
    padding: 34px;
    margin:23px;
    margin:auto;

}

.container h1,p{
    text-align:center;
    opacity: 0.7;

}

input,textarea{

    width:80%; 
    margin: 11px 0px;
    padding:7px;
    font-size: 16px;
    border:2px solid black;
    border-radius:6px;
    outline:none;
}
form{
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
}

.btn{
    color:white;
    background-color: purple;
    padding: 8px 12px;
    font-size: 20px;
    border:2px solid white;
    border-radius:14px;
    cursor:pointer;
}
.bg{
    width:100%;
    position:absolute;
    z-index:-1;
}

.submitMsg
{
    color:green;
}
  </style
</body>
</html>
