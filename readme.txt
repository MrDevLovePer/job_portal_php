user login
---------------
Step2: Now you login as candidate with following details
Email: oleg@test.com
Password: 123456
//Note1: There are 100 candadates users all with same password-123456
//Note2: All Password are encrpyted through code so you CANNOT change password directly from database.


Company login
-----------------
Email: lobortis@a.ca
Password: 123456
//Note1: There are 100 Companies account all with same password-123456
//Note2: All Password are encrpyted through code so you CANNOT change password directly from database.

admin login
-----------------
Username: admin
Password: 123456


If you are testing on real server then you can uncomment the following code from adduser.php

// Send Email
$to = {CANDIDATE_EMAIL ADDRESS};
$subject = "Job Portal - Confirm Your Email Address";
$message = '
    <html>
    	 <head>
		    <title>Confirm Your Email</title>
		</head>
		<body>
		    <p>Click Link To Confirm</p>
		    <a href="{YOUR_REAL_DOMAIL}/verify.php?token='.$hash.'&email='.$email.'">Verify Email</a>
		</body>
	</html>
';
$headers[] = 'MIME-VERSION: 1.0';
$headers[] = 'Content-type: text/html; charset=iso-8859-1';
$headers[] = 'To: '.$to;
$headers[] = 'From: hello@yourdomain.com';
// You can add more headers like Cc, Bcc;
$result = mail($to, $subject, $message, implode("\r\n", $headers)); // \r\n will return new line. 
if($result === TRUE) {
//If email sent successfully then Set some session variables and redirect to login page
	$_SESSION['registerCompleted'] = true;
	header("Location: login.php");
	exit();