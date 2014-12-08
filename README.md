index.html
==========

<!DOCTYPE html>
<head>
<title>Editing form</title>
<meta charset='windows-1251'>
<link rel="stylesheet" type="text/css" href="style.css">                                                    
<script type='text/javascript' src='http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js'></script>
<script src="http://code.jquery.com/jquery-1.10.2.js"></script>
<script src="http://code.jquery.com/ui/1.10.4/jquery-ui.js"></script>
	  
<script type='text/javascript'>   
$(document).ready(function(){
 
         $(function() {
		   $("#accordion").accordion({ header: "p", collapsible: true, active: false });
         });
  
  
  $("p").mouseover(function(){//Функция для меню. При наведении мыши, пункт меню меняет цвет.
    $(this).css("background-color","#cd5c5c");
	$(this).css("color","#F8F8FF");
  });
  $("p").mouseout(function(){
    $(this).css("background-color","#F8F8FF");
	$(this).css("color","#444");
  });
     
    $('#email').blur(function(){//Email проверка.
        if($(this).val() != '') {
            var pattern = /^([a-z0-9_\.-])+@[a-z0-9-]+\.([a-z]{2,4}\.)?[a-z]{2,4}$/i;
            if(pattern.test($(this).val())){
            } else {
                alert("Enter correct email!");
            }
        } else {
            alert("The field is empty. Enter email!");
        }
    });

});  

    function validateAge(input) {//Не допускает ввода никаких символов, кроме чисел.
	    input.value = input.value.replace(/[^\d,]/g, '');
    };	
    
    function validateText(input) {//Не допускает ввода никаких символов, кроме латинских букв.
	    input.value = input.value.replace(/[^a-z, A-Z]/, '');
    };	
   
   function checkPass() {//Проверка на равенство паролей. 
    var pass1 = document.getElementById("pass1").value;
    var pass2 = document.getElementById("pass2").value;
    var ok = true;
    if (pass1 != pass2) {
        alert("Passwords do not match!");
        document.getElementById("pass1").style.borderColor = "#CD5C5C";//При неверном вводе пароля, делаем границу красной.
        document.getElementById("pass2").style.borderColor = "#CD5C5C";
        ok = false;
    }else{
        document.getElementById("pass1").style.borderColor = "#F8F8FF";//При верном вводе пароля, делаем границу белой.
        document.getElementById("pass2").style.borderColor = "#F8F8FF";
	}
    return ok;
}
                                       
</script> 

</head>
<body>

<h1>Editing form</h1>

            <div id="accordion">
               <p>Home</p>
			    <div>
                  <ul>
                     <li>About</li>
                     <li>Our team</li>
                  </ul>
               </div>
			   <p>Personal data</p>
               <div>
                  <ul>
                     <li>View my profile</li>
                     <li>Edit my profile</li>
                  </ul>
               </div>
               <p>Contact us</p>
               <div>
                  <ul>
                     <li>Social nets</li>				  
                     <li>Looking for a job?</li>
                     <li>Contribute</li>
                     <li>Contacts</li>					 
                  </ul>
               </div>
            </div>
         </div>
  
<div class="form" >
<form onsubmit="return checkmail(this.email.value)" action="#" method="post">

Name:    <input type="text" placeholder="John" size="20" maxlength="30" onkeyup="validateText(this)" onchange="validateText(this)" required><br/>
Surname: <input type="text" placeholder="Dou" maxlength="40" onkeyup="validateText(this)" onchange="validateText(this)" required><br/>
Age:     <input type="text" placeholder="30" size="2" maxlength="2" onkeyup="return validateAge(this)" onchange="return validateAge(this)" required><br/>
Email:   <input id="email" type="email" placeholder="example@any.com" maxlength="30" required><br/><!--Некоторые пользователи отключают JS, поэтому я подстраховываюсь HTML-валидацией.-->
Country: <input type="text" placeholder="USA" maxlength="40" onkeyup="validateText(this)" onchange="validateText(this)" required><br/>
State:   <input type="text" placeholder="Nevada" maxlength="20" onkeyup="validateText(this)" onchange="validateText(this)"><br/>
City:    <input type="text" placeholder="Las Vegas" maxlength="20" onkeyup="validateText(this)" onchange="validateText(this)" required><br/>
Password:<input type="password" id="pass1" required><br/>
Repeate password:<input type="password" id="pass2" onblur="return checkPass()" required><br/>

<input type="button" id="submit" value="submit"><br/><br/>
</form>
</div>

</body>
</html>

