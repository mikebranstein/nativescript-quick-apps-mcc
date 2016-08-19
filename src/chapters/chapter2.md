## App 3: Data submission

### Main Page

<h4 class="exercise-start">
    <b>Demo</b>: Navigating to another page 
</h4>

Add a `<Button />` to the main page of the app.

```xml
<Page>
    <StackLayout>
        <Label text="Welcome to Tekmo!" class="title" />

        <Button id="contact-us" text="Contact Us" tap="onContactUsTap" />
    </StackLayout>
</Page>
```

Wire the button to navigate to the Contact Us page.

```javascript
var frameModule = require("ui/frame");

exports.onContactUsTap = function (args) {
    console.log("Navigating to the Contact Us page.");
    frameModule.topmost().navigate("contact-us");
};
```

<div class="exercise-end"></div>

### Building the Contact Us page

<h4 class="exercise-start">
    <b>Demo</b>: Navigating to another page 
</h4>

Add a Contact Us page with content.

```xml
<Page loaded="onLoaded">
    <StackLayout>
        <!-- title -->
        <Label text="Contact Us" class="title" />

        <!-- data submission -->
        <Label textWrap="true" text="Contact us by submitting a message below." />

        <TextField id="subject" hint="Enter a subject..." />
        <TextView id="message" hint="Enter a message..." />

        <Button text="Submit" tap="onTap" />

    </StackLayout>
</Page>
```

Add a Contact Us JavaScript page and code.

```javascript 
var httpModule = require("http");
var dialogModule = require("ui/dialogs");
var page;

// capture a reference to the current page after it loads
// we'll need this later to access the text boxes on the screen
exports.onLoaded = function onLoaded(args) {
    page = args.object;
};

exports.onTap = function onTap(args) {

    // step 1: get data out of text field and text view
    var subject = page.getViewById("subject").text;
    var message = page.getViewById("message").text;

    console.log("Submitting: " + subject + ", " + message);

    // step 2: submit data to Tekmo

    // step 2.1: assemble data to send
    var data = JSON.stringify({
        "subject": subject,
        "message": message
    });

    // step 2.2: send the request toa remote web service
    httpModule
        .request({
            url: "https://nstweet.brosteins.com/api/message",
            method: "POST",
            headers: { "Content-Type": "application/json" },
            content: data })
        .then(function(response) {
            // success: tell the user
            console.log("Received a response: HTTP " + response.statusCode);
            dialogModule.alert("Thank you for your feedback!");
        }, function(e) {
            // error: oh snap
            console.log("Error occurred: " + e);
            dialogModule.alert("We couldn't send your message right now. Try again later.");
        });
};
```

<div class="exercise-end"></div>

