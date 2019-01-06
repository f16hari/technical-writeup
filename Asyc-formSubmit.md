---
# How to submit an HTML FORM to the sever without RELOADING or REDIRECTING to the server page ?
#### 2019-04-01
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
so it creates a modal from as :![alt text](https://b3ejla.bn.files.1drv.com/y4mNZI9PpmS-nNolYoD8svisbxxOjQaebMrktC8F50AL2uJ4-O3P--nKXwXB--l4pM4ZzNLgtLa3qEHpAWseTVM9TzVE_ncwZF67nXlX-ybcUJ2jx4oxifs7Andtvux77sMHufd0HxsJoVNXqbUYfli-_Vl-8UqicddVSvIKYvh27WB3UU1v2NH3EufwznJdK8V5DC8cnYNmEG3A9NPJvNsWQ?width=1920&height=1080&cropmode=none)

on Click of the button we get the from modal as :
![alt text](https://lh5.googleusercontent.com/Kr0Z8ShF4_oUMnifmsPxtKmI5FZ8e5xX-oigr9LfwO9oIzlCdBTMXjFxqgnev4VPHum5C4wv4zspe_NBKG_l=w1402-h968-rwhttps://b3fuhw.bn.files.1drv.com/y4muzQl0aUjhkpmjxw0PlidO8np_6f_lXy3M6gHkPPTFo3vD1ktBEnnnWGivDv9HQgnh3RPK5wnB4K0COogq6aHEYEJZ9nZ7vCrF5iSdw2p7DMZtzntNzIP2V4c45tv8guIpMNLLf5jNkC3ARgM4UEONwvFYr-S7ejaxKkQHD68EFMc3g32IX_ZrAHB8H93EsSE39_GeZYLJk5Sj0_5fFyhHg?width=1920&height=1080&cropmode=none)

so the `JQuery` function to process submit is the following :
```javascript
function invoke()
		{
			console.log("asynchronus submission invoked");
			$("#submit").click(function(){

				$.ajax({
					type: "POST",
					url: "sampleServerPage.php",
					cache: false,
					success: function(){
						window.alert("Asynchronus submission sucessful");

							}
					});
			return false;
			});
		}
```

so the parameters that are to be considered are `type` - is used to specify the *Get* or *POST* method `url` - is used to specify the server page to process data, in my case it is *sampleServerPage.php* `cache` is either *true* or *false* depending on whether you want to store it in the browser cache or not `sucess` - the call back function that must be executed after sucessfull completion of the ajax request

So after completion it looks something like :![alt text](https://b3htqg.bn.files.1drv.com/y4mRIaw_RcBFMO1f1MJlfNUNqWrWG1nUsdFRzoeBnZs9wBRngr-C7Ya27qtkNlMNMelMv-v3_6phhJPfYvJhvoAWFZwq4aRM4RspG3etA66A0_r19AG-a3CP5tUyoE4Ml664T5bn_L9M6LNPtLy9GXOPmwz4xoOZkhts21CX10IrUGUNgvunmwpf6_6GZjNlIC-vtKSXvZpMEf6PGVABHXlxg?width=1920&height=1080&cropmode=none)

So That's it you can use this code as the base to handle your from data.
