---
# How to submit an HTML FORM to the sever without RELOADING or REDIRECTING to the server page ?
## '2019-04-01'
---

Seeing the title of this write up you may be wondering what is the big deal in form submission ?

But the thing that I want to convey is that the predominant way of submitting the form is an legacy way in which you just include an form tag of the HTML like the following
```HTML
<from action="sampleServerPage" method="get/post">
  ....
</form>
```
The above way of submitting details to the server causes the page to redirect to the `sampleSeverPage` in the `<action>` tag along with the loss of control of the current page. This might not be a big concern when working on simple web apps that require less desktop like functionality.

So, I am going to discuss a method that uses `Ajax` and `JQuery` to allow us to asynchronusly submit the data to the server without loosing control over the current page
for the implementation of the server functionality I will be using `PHP ^5.0.6`


consider the `<form>` be declared as
```HTML
<div id="form"> 
		<div class="modal-body">
			<div style="float:left;width:50%;">
            
            <input type="text" name="name" placeholder=" Name . . ."><br><br>
			<input type="tel" name="phno" placeholder=" Phno . . ."><br><br>
			<input type="email" name="email" placeholder=" Email . . ."><br><br>
			<textarea name="message" placeholder=" Type your msg here . . . " cols="23" rows="5"></textarea>
			
            </div>
			<div>
			After submitting you will be contacted by our one of our Hr's <br>
			Hr will explain course details and fees <br>
			we will send course details in email <br>
			Join the courses as soon as you are satisfied
			</div>
			<div class="clearfix"></div>
			
			
		</div>
		<div class="modal-footer">
			<input type="submit" id='submit' class="btn btn-primary" value="SUBMIT">
		</div>
</div>
```
