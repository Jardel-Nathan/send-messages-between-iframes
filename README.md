# send-messages-between-iframes

**CALL PARENT FUNCTION BY A CHILD IFRAME FUNCTION( IFRAME TO PARENT PAGE )**

in parent page:
```html

<iframe id="iframeId" src="https://yoursiteurl/"></iframe>

<script type="text/javascript">
   var eventMethod = window.addEventListener
    ? "addEventListener"
    : "attachEvent";
    var eventer = window[eventMethod];
    var messageEvent = eventMethod === "attachEvent"
    ? "onmessage"
    : "message";

    eventer(messageEvent, function (e) {       
        if (e.data=='nameFunction') {
            //execute function
        }
        console.log(e.data);
    });
</script>
```

In frame page:
```html
<button onclick="callParentFunction()">Call action</button>

<script type="text/javascript">
 function callParentFunction(){
  parent.postMessage('nameFunction', '*');
  }
</script>
```

**CALL IFRAME FUNCTION BY A PARENT PAGE( PARENT PAGE TO IFRAME )**

in parent page:
```html

<iframe id="iframeId" src="https://yoursiteurl/"></iframe>

<script type="text/javascript">
    function sendToIframe(){
        var iframeWindow = document.getElementById("iframeId").contentWindow;
        iframeWinWindow.postMessage('yor message value', "https://yoursiteurl/");
        return false;
    }
</script>
```

In frame page:
```html
<script type="text/javascript">
 function displayMessage (evt) {
    var message = evt.data;
    console.log(message)
    //your function 
}

if (window.addEventListener) {
    // For standards-compliant web browsers
    window.addEventListener("message", displayMessage, false);
}
else {
    window.attachEvent("onmessage", displayMessage);
}
</script>
```
