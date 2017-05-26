For example, we have a jsp containing this line of code: `<input type="text" name="address1" value="value1from">`  

If a use typed this into the value: `"/><script>alert(document.cookie)</script><!- ` or `"onfocus="alert(document.cookie)`,  

The whole line will become: `<input type="text" name="address1" value=""/><script>alert(document.cookie)</script><!- ">`   
or `<input type="text" name="address1" value="" onfocus="alert(document.cookie)">`  

This is XSS(Cross Site Scripting), data becomes code, it's dangerous as it may cause the leak of user data. In this case, we need some HTML 
encode, 
