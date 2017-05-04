# Search

## Search Packages

This endpoint searches all packages.

```http
GET /search/package?q=foo HTTP/1.1
Host: registry.diamond.js.org
```

> The above request returns JSON structured like this:

```json
{
  "size": 1,
  "packages": [
    {
      "name": "foo",
      "description": "Foo!",
      "createdAt": "2017-05-01T18:58:51.395Z",
      "updatedAt": "2017-05-01T18:58:51.395Z",
      "tags": {
        "latest": "0.1.0"
      },
      "authors": [
        {
          "username": "hackzzila",
          "email": "admin@hackzzila.com",
          "createdAt": "2017-05-01T18:58:47.263Z"
        }
      ],
      "versions": {
        "0.1.0": {
          "version": "0.1.0",
          "data": {
            "name": "foo",
            "version": "0.1.0",
            "description": "Foo!",
            "main": "index.sass",
            "author": "Hackzzila",
            "license": "MIT",
            "dependencies": {
              "bootstrap": "^4.0.0"
            }
          },
          "readme": "# foo\nFoo!",
          "createdAt": "2017-05-01T18:59:18.726Z",
          "dist": {
            "shasum": "ba25121304c70b5db67926521894965abf2412f7b2aa1ee6b505ea70571f058f",
            "url": "https://registry.diamond.js.org/package/foo/0.1.0"
          }
        }
      }
    }
  ]
}

```

### HTTP Request

`GET /search/package`

### Query Parameters
| Key | Type | Description |
|-----|------|-------------|
| q | string | The search query |

### Reponse Format

An array of [Package Objects](#package-object) is returned including all keys.



## Search Users

This endpoint searches all users.

```http
GET /search/package?q=hackzzila HTTP/1.1
Host: registry.diamond.js.org
```

> The above request returns JSON structured like this:

```json
{
  "size": 1,
  "users": [
    {
      "username": "hackzzila",
      "email": "admin@hackzzila.com",
      "createdAt": "2017-05-01T18:58:47.263Z",
      "packages": [
        "foo"
      ]
    }
  ]
}

```

### HTTP Request

`GET /search/user`

### Query Parameters
| Key | Type | Description |
|-----|------|-------------|
| q | string | The search query |

### Reponse Format

An array of [User Objects](#user-object) is returned including all keys.