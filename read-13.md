# Readings: Sending Form Data
## Read:13 - Update/Delete

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-13).

### For this class, I will be reading from this resource: `Sending Form Data` .

### :pushpin: [Sending Form Data](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data)


## Doc: Sending Form Data


### Client/server architecture

At it's most basic, the web uses a client/server architecture that can be summarized as follows. a client (usually a web browser) sends a request to a server (most of the time a web server like Apache, Nginx, IIS, Tomcat, etc.), using the HTTP protocol. The server answers the request using the same protocol.

![](https://developer.mozilla.org/files/4291/client-server.png)


### On the client side: defining how to send the data

The `<form>` element defines how the data will be sent. All of its attributes are designed to let you configure the request to be sent when a user hits a submit button. The two most important attributes are `action` and `method`.


### The action attribute

The `action` attribute defines where the data gets sent. Its value must be a valid relative or absolute URL. If this attribute isn't provided, the data will be sent to the URL of the page containing the form — the current page.


In this example, the data is **sent** to an absolute URL — https://example.com:
```
<form action="https://example.com">
```

Here,a relative URL — the data is sent to a different URL on the same origin:

```
<form action="/somewhere_else">
```

The names and values of the non-file form controls are sent to the server as `name=value` pairs joined with ampersands. The `action` value should be a file on the server that can handle the incoming data, including ensuring server-side validation. 


### The method attribute

The `method` attribute defines how data is sent. The HTTP protocol provides several ways to perform a request; HTML form data can be transmitted via a number of different methods, the most common being the `GET` method and the `POST` method.


**The GET method**

The `GET method` is the method used by the browser to ask the server to send back a given resource: "Hey server, I want to get this resource." In this case, the browser sends an empty body. Because the body is empty, if a form is sent using this method the data sent to the server is appended to the URL.


**The POST method**

The POST method is a little different. It's the method the browser uses to talk to the server when asking for a response that takes into account the data provided in the body of the HTTP request: "Hey server, take a look at this data and send me back an appropriate result." If a form is sent using this method, the data is appended to the body of the HTTP request.


### Viewing HTTP requests

HTTP requests are never displayed to the user (if you want to see them, you need to use tools such as the Firefox Network Monitor or the Chrome Developer Tools). As an example, your form data will be shown as follows in the Chrome Network tab. After submitting the form:

   1. Open the developer tools.
   2. Select "Network"
   3. Select "All"
   4. Select "foo.com" in the "Name" tab
   5. Select "Headers"


### The enctype attribute

This attribute lets you specify the value of the `Content-Type` HTTP header included in the request generated when the form is submitted. This header is very important because it tells the server what kind of data is being sent. By default, its value is `application/x-www-form-urlencoded`. In human terms, this means: "This is form data that has been encoded into URL parameters."

If you want to send files, you need to take three extra steps:

  - Set the `method` attribute to `POST` because file content can't be put inside URL parameters.
  - Set the value of `enctype` to `multipart/form-data` because the data will be split into multiple parts, one for each file plus one for the text data included in the form body (if text is also entered into the form).
  - Include one or more `<input type="file">` controls to allow your users to select the file(s) that will be uploaded.
   

### Be paranoid: Never trust your users

All data that comes to your server must be checked and sanitized. Always. No exception.

  - **Escape potentially dangerous characters**. The specific characters you should be cautious with vary depending on the context in which the data is used and the server platform you employ, but all server-side languages have functions for this. Things to watch out for are character sequences that look like executable code (such as JavaScript or SQL commands).
  - **Limit the incoming amount of data to allow only what's necessary**.
  - **Sandbox uploaded files**. Store them on a different server and allow access to the file only through a different subdomain or even better through a completely different domain.
