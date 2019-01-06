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
            		<input type="text"><br><br>
			<input type="text"><br><br>
			....
			<input type="text" ><br><br>
			
			<div>
			 ....
			</div>
			
		</div>
		<div class="modal-footer">
			<input type="submit" id='submit' class="btn btn-primary" value="SUBMIT">
		</div>
</div>
```
so it creates a modal from as :![alt text](https://drive.google.com/file/d/1iXcFlppPzXXlhQMqtIwqeU--TN9V572k/view?usp=sharing)
