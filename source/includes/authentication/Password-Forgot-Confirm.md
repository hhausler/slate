<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->
## Confirm Password Reset

### POST /password/forgot/confirm

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --request POST 'https://api.nelnet.io/authapi/password/forgot/confirm' \
--header 'Content-Type: application/json' \
--header 'userpoolid: <USERPOOLID>' \
--header 'appclientid: <APPCLIENTID>' \
--data-raw '{"userName":"<USERNAME>","verificationCode":"<VERIFICATIONCODE>","newPassword":"<NEWPASSWORD>"}'
```

```csharp
var client = new RestClient("https://api.nelnet.io/authapi/password/forgot/confirm");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("userpoolid", "<USERPOOLID>");
request.AddHeader("appclientid", "<APPCLIENTID>");
var body = @"{""userName"":""<USERNAME>"",""verificationCode"":""<VERIFICATIONCODE>"",""newPassword"":""<NEWPASSWORD>""}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = JSON.stringify({
  "userName": "<USERNAME>",
  "verificationCode": "<VERIFICATIONCODE>",
  "newPassword": "<NEWPASSWORD>"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/authapi/password/forgot/confirm");
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
  "userName": "<USERNAME>",
  "verificationCode": "<VERIFICATIONCODE>",
  "newPassword": "<NEWPASSWORD>"
})
headers = {
  'Content-Type': 'application/json',
  'userpoolid': '<USERPOOLID>',
  'appclientid': '<APPCLIENTID>'
}
conn.request("POST", "/authapi/password/forgot/confirm", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
  "data": {
    "userName": "string",
    "passwordChanged": true
  }
}
```

<!-- LEFT: documentation -->

Confirm password reset.

<!-- Use <aside class="notice"></aside> to add notices if needed -->

### HTTP Request

`POST https://api.nelnet.io/authapi/password/forgot/confirm`

Header Key | Info
---------- | -------
userpoolid | Velocity User Pool ID.
appclientid | Velocity Client ID.

Body Parameter | Info
---------- | -------
userName | The username.
verificationCode | The verfiication code.
newPassword | The new password.

### HTTP Response

Data | Info
---------- | -------
userName | The username.
passwordChanged | Boolean confirmation of the password change.
