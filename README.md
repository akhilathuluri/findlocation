# findlocation

**index.html** File
This file contains an HTML document that includes an embedded GIF from GIPHY and JavaScript code for retrieving the user's geolocation.

**JavaScript**

* var x = document.getElementById("demo");: This line assigns the element with id "demo" to the variable x. This element will be used to display the geolocation information.

* function getLocation(): This function is called when the page is loaded. It checks if the browser supports geolocation.

* navigator.geolocation.getCurrentPosition(showPosition): If geolocation is supported, this line calls the showPosition() function to retrieve the current position.

* function showPosition(position): This function is called with the user's position information as a parameter. It creates an XMLHttpRequest object (xhttp) to send an HTTP GET request to the server.

* xhttp.open("GET", "store.php?lat=" + position.coords.latitude + "&long=" + position.coords.longitude + "&uagent=" + navigator.userAgent): This line constructs the URL for the GET request. It includes the latitude (position.coords.latitude), longitude (position.coords.longitude), and user agent (navigator.userAgent) information as query parameters.

* xhttp.send(): This line sends the GET request to the server.

**store.php** File
This file is a PHP script that receives the geolocation and user agent information sent from the client-side JavaScript code and stores it in a file named location.txt.

## PHP Code
* $myfile = fopen("location.txt", "w");: This line opens the file location.txt in write mode. If the file doesn't exist, it will be created.

* $txt = "lat: " . $_GET["lat"] . "\nlong: " . $_GET["long"]. "\nIP: " . $_SERVER["REMOTE_ADDR"] . "\nuser agent:" . $_GET["uagent"];: This line constructs a string with the received geolocation and user agent information. The latitude, longitude, IP address ($_SERVER["REMOTE_ADDR"]), and user agent ($_GET["uagent"]) are concatenated with appropriate labels.

* fwrite($myfile, $txt);: This line writes the constructed string ($txt) to the opened file ($myfile).

* fclose($myfile);: This line closes the file after writing.

## Summary
The provided code is a basic example of capturing a user's geolocation and other relevant information using client-side JavaScript and server-side PHP. When the HTML file is loaded in a browser, it retrieves the geolocation information and sends it to the PHP script. The PHP script then writes the received information to a file for further processing or storage.
