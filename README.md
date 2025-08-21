<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Bootstrap Form Example</title>
    <!-- jQuery File Upload -->
  <script src="JS/jquery-3.5.1.min.js"></script>

  <!-- Bootstrap CSS -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css"
    integrity="sha384-xOolHFLEh07PJGoPkLv1IbcEPTNtaed2xpHsD9ESMhqIYd0nLMwNLD69Npy4HI+N" crossorigin="anonymous">

  <!-- Bootstrap JS Bundle -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/js/bootstrap.bundle.min.js"
    integrity="sha384-Fy6S3B9q64WdZWQUiU+q4/2Lc9npb8tCaSX9FK7E8HnRr0Jz8D6OP9dO5Vg3Q9ct" crossorigin="anonymous"></script>
<style>
	span{
		color: darkred;
	}
</style>


  <script>
    var arr=[];
  		$(document).ready(function(){
  			//alert("DOM Load");
  			$("#btnsubmit").click(function(){
  				$("#err_id").empty();
  			          $("#err_name, #err_mobile, #err_email, #err_password").text("");
        //validation code
        if($("#txtid").val().trim()==""){
          $("#err_id").text("Id is mandatory!");
          $("#txtid").focus();
          return;
        }  

        if($("#txtname").val().trim()==""){
          $("#err_name").text("Name is mandatory!");
          $("#txtname").focus();
          return;
        }
        if($("#txtmobile").val().trim()==""){
          $("#err_mobile").text("Mobile is mandatory!");
          $("#txtmobile").focus();
         return;
        }
        if($("#txtemail").val().trim()==""){
          $("#err_email").text("Email is mandatory!");
          $("#txtemail").focus();
         return;
        }
        if($("#txtpassword").val().trim()==""){
          $("#err_password").text("Password is mandatory!");
          $("#txtpassword").focus();
           return;
        }	
  		
  			
  				var gen="female"
  				if($("#rdomale").checked){
  					gen="male";
  				}
  				var sub = [];
if ($("#chkpolitics").is(":checked")) {
    sub.push("Politics");
}
if ($("#chksports").is(":checked")) {
    sub.push("Sports");
}
if ($("#chkai").is(":checked")) {
    sub.push("Artificial Intelligence");
}
var subj = sub.join(",");
  				//var subj=sub.join(",")
  				
  				var obj={
  					"Id":$("#txtid").val(),
  					"Name":$("#txtname").val(),
  					"Mobile":$("#txtmobile").val(),
  					"Email":$("#txtemail").val(),
  					"Gender":gen,
  					"Subject":subj,
  					"Country":$("#txtcountry").val()
  				}
          
  				arr.push(obj);
          loaddata();
  				console.log(arr);
        
  			});
  		});

      function loaddata(){
       $("#frm")[0].reset();
          $("#tbdy").empty();
          for(var i=0;i<arr.length;i++){
            $("#tbdy").append(`<tr><td>${arr[i].Id}</td>
          <td>${arr[i].Name}</td>
          <td>${arr[i].Mobile}</td>
            <td>${arr[i].Email}</td>
          <td>${arr[i].Gender}</td>
              <td>${arr[i].Subject}</td>
              <td>${arr[i].Country}</td>
              <td><input type="button" class="bg-danger" value="Delete"></td>
              <input type="button" class="bg-info" value="Edit">
          </tr>`)

          }
      

      
      }
      
  </script>
</head>
<body>
  <div class="container-fluid">
    
    <!-- Navbar Row -->
    <div class="row">
      <div class="col-12">
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
          <div class="container-fluid">
            <a class="navbar-brand" href="#">MyWebsite</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav"
              aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
            </button>
            
            <div class="collapse navbar-collapse" id="navbarNav">
              <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                  <a class="nav-link active" href="#">Home</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link" href="#">About</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link" href="#">Services</a>
                </li>
                <li class="nav-item">
                  <a class="nav-link" href="#">Contact</a>
                </li>
              </ul>
            </div>
          </div>
        </nav>
      </div>
    </div>

    <!-- Form Row -->
    <div class="row mt-4">
      <div class="col-4">
        <form id="frm">
          
          <div class="mb-3">
            <label for="txtname" class="form-label" readonly>ID*</label>
            <input type="text" class="form-control" id="txtid" placeholder="Enter your id">
            <span id="err_id"></span>
          </div>
          <!-- Name -->
          <div class="mb-3">
            <label for="txtname" class="form-label">Name*</label>
            <input type="text" class="form-control" id="txtname" placeholder="Enter your name">
            <span id="err_name"></span>
          </div>

          <div class="mb-3">
            <label for="txtname" class="form-label">Mobile Number*</label>
            <input type="text" class="form-control" id="txtmobile" placeholder="Enter your Mobile Number">
            <span id="err_mobile"></span>
          </div>

          <!-- Email -->
          <div class="mb-3">
            <label for="txtemail" class="form-label">Email*</label>
            <input type="email" class="form-control" id="txtemail" placeholder="Enter your email">
            <small class="form-text text-muted">We'll never share your email with anyone else.</small>
            <span id="err_email"></span>
          </div>

          <!-- Gender -->
          <div class="mb-3">
            <label>Select Gender</label><br>
            <input type="radio" id="rdomale" name="rdogender" value="male"> Male
            <input type="radio" id="rdofemale" name="rdogender" value="female"> Female
          </div>

          <div class="mb-3">
            <label>Select Subjects</label><br>
            <input type="checkbox" id="chkpolitics" name="chkpolitics" value="politics"> Politics
			<input type="checkbox" id="chksports" name="chksports" value="sports"> Sports
			<input type="checkbox" id="chkai" name="checkai" value="ai">Artificial Intelligence
          </div>

          <!-- Password -->
          <div class="mb-3">
            <label for="txtpassword" class="form-label">Password*</label>
            <input type="password" class="form-control" id="txtpassword" placeholder="Enter password">
            <span id="err_password"></span>
          </div>

          <!-- Checkbox -->
          <div class="mb-3 form-check">
            <input type="checkbox" class="form-check-input" id="txtterms">
            <label class="form-check-label" for="txtterms">I agree to the terms</label>
          </div>

          <!-- Country -->
          <div class="mb-3">
            <label for="txtcountry" class="form-label">Country</label>
            <select class="form-control" id="txtcountry">
              <option selected>Select your country</option>
              <option value="India">India</option>
              <option value="USA">USA</option>
              <option value="UK">UK</option>
            </select>
          </div>

          <!-- Submit Button -->
          <div class="d-flex justify-content-center">
            <button type="button" id="btnsubmit" class="btn btn-primary">Submit</button>
          </div>

        </form>
      </div>
    
    <div class="col-8">
    	<div class="row"><div class="col-12 d-flex justify-content-center"><b><h5>Registration Form</h5></b></div></div>
    	  <table class="table table-bordered">
      <thead class="thead-dark">
        <tr>
			     <th>ID</th>
          <th>Name</th>
          <th>Email</th>
          <th>Subject</th>
          <th>Gender</th>
          <th>Course</th>
          <th>Country</th>
        </tr>
      </thead>
      <tbody id="tbdy">
        
      </tbody>
    </table>
    </div>
    </div>
  </div>
</body>
</html>
