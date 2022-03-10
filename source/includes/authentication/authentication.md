# Authentication

Use the Authentication service to authenticate in Velocity, allowing you to call our endpoints.

Velocity expects the bearer token to be included in all API requests to the server in a header that looks like this:

`Authorization: Bearer {{accessToken}}`

## Authenticate
<!-- RIGHT -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/authapi/authenticate \
  -H 'Content-Type: application/json' \
  -H 'userpoolid: <USERPOOLID>' \
  -H 'appclientid: <APPCLIENTID>' \
  -H 'cache-control: no-cache' \
  -d '{
  "userName": "<USERNAME>",
  "password": "<PASSWORD>"
}'
```

```csharp
var client = new RestClient("https://api.nelnet.io/authapi/authenticate");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("userpoolid", "<USERPOOLID>");
request.AddHeader("appclientid", "<APPCLIENTID>");

request.AddParameter("undefined", "{\n  \"userName\": \"<USERNAME>\",\n  \"password\": \"<PASSWORD>\"\n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```javascript
var data = JSON.stringify({
  "userName": "<USERNAME>",
  "password": "<PASSWORD>"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/authapi/authenticate");
xhr.setRequestHeader("userpoolid", "<USERPOOLID>");
xhr.setRequestHeader("appclientid", "<APPCLIENTID>");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = "{\n  \"userName\": \"<USERNAME>\",\n  \"password\": \"<PASSWORD>\"\n}"

headers = {
    'userpoolid': "<USERPOOLID>",
    'appclientid': "<APPCLIENTID>",
    'Content-Type': "application/json",
    'cache-control': "no-cache"
    }

conn.request("POST", "authapi,authenticate", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "accessToken": "eyJraW...P1MAcg",
        "tokenType": "Bearer",
        "issuedAt": 1549296343,
        "expiresIn": 1549299943
    }
}
```

<!-- LEFT -->
Get a bearer token to be used with API calls.

### HTTP Request

`POST https://api.nelnet.io/authapi/authenticate`

Header Key | Info
---------- | -------
userpoolid | Velocity User Pool ID.
appclientid | Velocity Client ID.

Body Parameter | Info
---------- | -------
userName | Velocity Username.
password | Velocity Password.

### HTTP Response

Data | Info
---------- | -------
accessToken | The access token is a JSON Web Token (JWT) that contains claims about the identity of the authenticated user such as name, role, email, and phone_number.
tokenType | Type of token used with API calls.
issuedAt | Time the token was issued representing the number of seconds from 1970-01-01T0:0:0Z as measured in UTC format until the date/time.
expiresIn | Time the token will expire representing the number of seconds from 1970-01-01T0:0:0Z as measured in UTC format until the date/time.
