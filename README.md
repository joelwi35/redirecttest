# redirecttest
Sample project that test out the http 307 temp redirect behavior. Also happens to call Walmart.com and trigger it's Perimeter-X safeguard.

First, run the redirect_test, by typing "node app.js" in a console while in that project directory.  This should start up the redirection controller service on your local machine on port 3000.

Next bring up the test.html page in the redirect_test_page project. In VSCode I do this by right-clicking on the test.html file and selecting "Open with Edge".

The web page will present you with 3 buttons to choose from with a high level label but no URL link resides behind any of the buttons. Once a button is select, it calls the redirect controller with it's button label, and the redirect controller sends back a URL to a resource that aligns with that label. 

You can change them, but the redirect controller currently maps the following:

| Label      | Redirect URL      |
| ------------- | ------------- |
| videogames | https://www.metacritic.com/games |
| comicstrip | https://dilbert.com |
| Walmart | https://walmart.com |

The redirect controller will return an http 307 with those URLs in the response's location header. This will trigger the browser to invoke the URL and send the flow directly to those endpoints instead. 

It will appear that those buttons are directly tied to those endpoints, but they are not. If you stop the redirect controller service, clicking those buttons will not fail to find any resource and will return a 404. Try it out!
