# Package

## Package Object
```json
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
```

Key | Type | Description
--------- | ------- | -----------
name | string | The package name
description | string | The latest version's description
createdAt | date | When the package was created
editedAt | date | When the package was last updated
tags | Object\<string, [SemVer](http://semver.org/)> | An object mapping tag names to version numbers. **May be empty on some package objects**
authors | Array\<[User](#user-object)> | An array of all package authors. **May be empty on some package objects**
versions | Object\<[SemVer](http://semver.org/), [Version](#version-object)> | An object mapping version numbers to version objects. **May be empty or not full on some package objects**



## Version Object
```json
{
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
```

Key | Type | Description
--------- | ------- | -----------
version | [SemVer](http://semver.org/) | The version
data | Object\<string, *> | The `package.json` contents
readme | string | The version's readme markdown content
createdAt | date | When the version was created
dist | [Dist](#dist-object) | The download information



## Dist Object
```json
{
  "shasum": "ba25121304c70b5db67926521894965abf2412f7b2aa1ee6b505ea70571f058f",
  "url": "https://registry.diamond.js.org/package/foo/0.1.0"
}
```

Key | Type | Description
--------- | ------- | -----------
shasum | sha256sum | The `sha256sum` for the tarball
url | string | A link to where to download the package



## Get Package

This endpoint gets a package by name.

```http
GET /package/foo HTTP/1.1
Host: registry.diamond.js.org
```

> The above request returns JSON structured like this:

```json
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
```

### HTTP Request

`GET /package/:name`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |

### Reponse Format

A [Package Object](#package-object) is returned including all keys.



## Download Package

This endpoint gets package contents.

```http
GET /package/foo/0.1.0 HTTP/1.1
Host: registry.diamond.js.org
```

> The above request returns a gzipped tarball (`.tar.gz`)

### HTTP Request

`GET /package/:name/:version`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to download |
| version | [SemVer](http://semver.org/) &#124; string | The version or tag that you want to download |

### Reponse Format

A gzipped tarball (`.tar.gz`) file is returned.



## Create Package Version

<aside class="notice">Requires authentication</aside>

This endpoint creates a package if it doesn't exist, and adds a version.

```http
POST /package/foo HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="package"; filename=""
Content-Type: "application/json"

{
  "name": "foo",
  "version": "0.1.0",
  "description": "Foo!",
  "main": "index.sass",
  "author": "Hackzzila",
  "license": "MIT",
  "dependencies": {
    "bootstrap": "^4.0.0"
  }
}

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="dist"; filename=""
Content-Type: "application/gzip"

GZIP CONTENTS

------WebKitFormBoundary7MA4YWxkTrZu0gW--
```

> The above request returns JSON structured like this:

```json
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
```

### HTTP Request

`POST /package/:name`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to add |

### Request Parameters
These params must be `multipart/form-data`

| Key | Type | Optional | Description |
|-----|------|----------|-------------|
| package | file | ❌ | `package.json` contents |
| readme | file | ✅ | `readme.md` contents |
| dist | file| ❌ | A gzipped tarball containing all files to be published |

### Reponse Format

A [Package Object](#package-object) is returned including all keys.



## Delete Package

<aside class="notice">Requires authentication</aside>

This endpoint deletes a package.

```http
DELETE /package/foo HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
```

> The above request returns nothing.

### HTTP Request

`DELETE /package/:name`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to delete |

### Reponse Format

No data is returned.



## Delete Package Version

<aside class="notice">Requires authentication</aside>

This endpoint deletes a package version.

```http
DELETE /package/foo/0.1.0 HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
```

> The above request returns nothing.

### HTTP Request

`DELETE /package/:name/:version`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |
| version | [SemVer](http://semver.org/) | The version that you want to delete |

### Reponse Format

No data is returned.



## Add Package Author

<aside class="notice">Requires authentication</aside>

This endpoint adds an author to a package.

```http
POST /package/foo/author/bar HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
```

> The above request returns JSON structured like this:

```json
{
  "name": "foo",
  "description": "Foo!",
  "createdAt": "2017-05-01T18:58:51.395Z",
  "updatedAt": "2017-05-01T18:58:51.395Z",
  "tags": {},
  "authors": [
    {
      "username": "hackzzila",
      "email": "admin@hackzzila.com",
      "createdAt": "2017-05-01T18:58:47.263Z"
    },
    {
      "username": "bar",
      "email": "bar@foo.baz",
      "createdAt": "2017-05-01T18:58:47.263Z"
    }
  ],
  "versions": {}
}
```

### HTTP Request

`POST /package/:name/author/:user`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |
| user | string | The username of the user you want to add |

### Reponse Format

A partial [Package Object](#package-object) is returned including the authors key.



## Remove Package Author

<aside class="notice">Requires authentication</aside>

This endpoint removes a package author.

```http
DELETE /package/foo/author/bar HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
```

> The above request returns JSON structured like this:

```json
{
  "name": "foo",
  "description": "Foo!",
  "createdAt": "2017-05-01T18:58:51.395Z",
  "updatedAt": "2017-05-01T18:58:51.395Z",
  "tags": {},
  "authors": [
    {
      "username": "hackzzila",
      "email": "admin@hackzzila.com",
      "createdAt": "2017-05-01T18:58:47.263Z"
    }
  ],
  "versions": {}
}
```

### HTTP Request

`DELETE /package/:name/author/:user`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |
| user | string | The username of the user you want to delete |

### Reponse Format

A partial [Package Object](#package-object) is returned including the authors key.



## Add/Edit Package Tag

<aside class="notice">Requires authentication</aside>

This endpoint adds or edits tag.

```http
POST /package/foo/tag/baz HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
Content-Type: application/json

{
  "version": "0.1.0"
}
```

> The above request returns JSON structured like this:

```json
{
  "name": "foo",
  "description": "Foo!",
  "createdAt": "2017-05-01T18:58:51.395Z",
  "updatedAt": "2017-05-01T18:58:51.395Z",
  "tags": {
    "latest": "0.1.0",
    "baz": "0.1.0"
  },
  "authors": [],
  "versions": {}
}
```

### HTTP Request

`POST /package/:name/tag/:tag`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |
| tag | string | The name of the tag you want to add/edit |

### Request Parameters 
| Key | Type | Description |
|-----|------|-------------|
| version | [SemVer](http://semver.org/) | The version you want to set the tag to |

### Reponse Format

A partial [Package Object](#package-object) is returned including the tags key.



## Remove Package Tag

<aside class="notice">Requires authentication</aside>

This endpoint removes a package tag.

```http
DELETE /package/foo/tag/baz HTTP/1.1
Host: registry.diamond.js.org
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw=
```

> The above request returns JSON structured like this:

```json
{
  "name": "foo",
  "description": "Foo!",
  "createdAt": "2017-05-01T18:58:51.395Z",
  "updatedAt": "2017-05-01T18:58:51.395Z",
  "tags": {
    "latest": "0.1.0"
  },
  "authors": [],
  "versions": {}
}
```

### HTTP Request

`DELETE /package/:name/author/:tag`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |
| tag | string | The name of the tag you want to delete |

### Reponse Format

A partial [Package Object](#package-object) is returned including the tags key.