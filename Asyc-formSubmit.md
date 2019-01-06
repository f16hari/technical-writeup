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
so it creates a modal from as :![alt text](https://lh3.googleusercontent.com/QyhBnyy5nQRhkwl9ZGWpzqgt8CrdU2Bfulpv_R3FK3T0mfwUn_DN2KEMy5SNMPfSSuZm1De6_kvY3FDyzVSQ=w1920-h968-rw)

on Click of the button we get the from modal as :
![alt text](https://lh5.googleusercontent.com/Kr0Z8ShF4_oUMnifmsPxtKmI5FZ8e5xX-oigr9LfwO9oIzlCdBTMXjFxqgnev4VPHum5C4wv4zspe_NBKG_l=w1402-h968-rw)

so the `JQuery` function to process submit is the following :
```javascript
function invoke()
		{
			console.log("asynchronus submission invoked");
			$("#submit").click(function(){

				$.ajax({
					type: "POST",
					url: "enquiry.php",
					cache: false,
					success: function(){
						window.alert("Asynchronus submission sucessful");

							}
					});
			return false;
			});
		}
```

