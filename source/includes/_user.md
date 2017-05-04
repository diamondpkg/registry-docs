# User

## User Object
```json
{
  "username": "hackzzila",
  "email": "admin@hackzzila.com",
  "createdAt": "2017-05-01T18:58:47.263Z",
  "packages": [
    "registry"
  ]
}
```

Key       | Type           | Always Present | Description
--------- | -------------- | -------------- | -----------
username  | string         | ✅ | The user's username
email     | string         | ✅ | The user's email
createdAt | date           | ✅ | When the user was created
packages  | Array\<string> | ❌ | All packages the user is an author of. **May not be present on all user objects**

## Get Current Logged in User

<aside class="notice">Requires authentication</aside>

This endpoint returns the current logged in user.

```http
GET /user HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw==
```

> The above request returns JSON structured like this:

```json
{
  "username": "hackzzila",
  "email": "admin@hackzzila.com",
  "createdAt": "2017-05-01T18:58:47.263Z",
  "packages": [
    "registry"
  ]
}
```

### HTTP Request

`GET /user`

### Reponse Format

A [User Object](#user-object) is returned including the `packages` key.



## Get User

This endpoint gets a user by username.

```http
GET /user/hackzzila HTTP/1.1
Host: registry.diamond.js.org
```

> The above request returns JSON structured like this:

```json
{
  "username": "hackzzila",
  "email": "admin@hackzzila.com",
  "createdAt": "2017-05-01T18:58:47.263Z",
  "packages": [
    "registry"
  ]
}
```

### HTTP Request

`GET /user/:name`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the user you want to get |

### Reponse Format

A [User Object](#user-object) is returned including the `packages` key.