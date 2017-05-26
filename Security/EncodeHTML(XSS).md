For example, we have a jsp containing this line of code: `<input type="text" name="address1" value="value1from">`  

If a use typed this into the value: `"/><script>alert(document.cookie)</script><!- ` or `"onfocus="alert(document.cookie)`,  

The whole line will become: `<input type="text" name="address1" value=""/><script>alert(document.cookie)</script><!- ">`   
or `<input type="text" name="address1" value="" onfocus="alert(document.cookie)">`  

This is XSS(Cross Site Scripting), data becomes code, it's dangerous as it may cause the leak of user data. In this case, we need some HTML encode:  

![HTML ENCODE](https://github.com/adrrrrrrrian/notes/blob/master/Security/1111.PNG)


Also, for the difference between HTML encoding and URL encoding:   
If you use HTML encoding for `id=123`, nothing will change. But for `<br/>`, you will get `&lt;br/&gt;`. It's escaping special characters.  
For URL encoding, if you do it for `id=123`, you will get `id%3d123`, and for `<br/>`, you will get `%3cbr%2f%3e`.  
