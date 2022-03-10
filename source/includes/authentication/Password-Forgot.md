<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->
## Forgot Password

### POST /password/forgot

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --request POST 'https://api.nelnet.io/authapi/password/forgot' \
--header 'Content-Type: application/json' \
--header 'userpoolid: <USERPOOLID>' \
--header 'appclientid: <APPCLIENTID>' \
--data-raw '{"userName": "<USERNAME>"}'
```

```csharp
var client = new RestClient("https://api.nelnet.io/authapi/password/forgot");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("userpoolid", "<USERPOOLID>");
request.AddHeader("appclientid", "<APPCLIENTID>");
var body = @"{""userName"": ""<USERNAME>""}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = JSON.stringify({
  "userName": "<USERNAME>"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/authapi/password/forgot");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("userpoolid", "<USERPOOLID>");
xhr.setRequestHeader("appclientid", "<APPCLIENTID>");

xhr.send(data);
```

```python
import http.client
import json

conn = http.client.HTTPSConnection("api.nelnet.io")
payload = json.dumps({
  "userName": "<USERNAME>"
})
headers = {
  'Content-Type': 'application/json',
  'userpoolid': '<USERPOOLID>',
  'appclientid': '<APPCLIENTID>'
}
conn.request("POST", "/authapi/password/forgot", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "message": "string"
    }
}
```

<!-- LEFT: documentation -->

Perform a password reset on a user account.

<!-- Use <aside class="notice"></aside> to add notices if needed -->

### HTTP Request

`POST https://api.nelnet.io/authapi/password/forgot`

Header Key | Info
---------- | -------
userpoolid | Velocity User Pool ID.
appclientid | Velocity Client ID.

Body Parameter | Info
---------- | -------
userName | The username.

### HTTP Response

Data | Info
---------- | -------
message | A string containing the message data.
