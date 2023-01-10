**Session Storage**
===

> The Session Storage is designed for scenarios where the user is carrying out a single transaction, but could be carrying out multiple transactions in different windows at the same time.

HTML5 introduces the sessionStorage attribute which would be used by the sites to add data to the session storage, and it will be accessible to any page from the same site opened in that window, i.e., session and as soon as you close the window, the session would be lost.

```html
<!DOCTYPE HTML>
<html>
   <body>
      <script type = "text/javascript">
         
         if( sessionStorage.hits ) {
            sessionStorage.hits = Number(sessionStorage.hits) +1;
         } else {
            sessionStorage.hits = 1;
         }
         document.write("Total Hits :" + sessionStorage.hits );
      </script>
	
      <p>Refresh the page to increase number of hits.</p>
      <p>Close the window and open it again and check the result.</p>

   </body>
</html>
```
