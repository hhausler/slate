<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->
## Overview Description

### VERB /shortened endpoint

<!-- RIGHT: code samples -->

> Sample request:

```shell
```

```csharp
```

```javascript
```

```python
```

> JSON returned:

```json
```

<!-- LEFT: documentation -->

**Sentence overview.**

<!-- Use <aside class="notice"></aside> to add notices if needed -->

### HTTP Request

`POST https://api.nelnet.io/`

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
userName | The username.
oldPassword | The password before the change.
newPassword | The new password after the change.
