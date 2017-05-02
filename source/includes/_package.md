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

This endpoint gets a package by name.

### HTTP Request

`GET /package/:name`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to get |

### Reponse Format

A [Package Object](#package-object) is returned including all keys.



## Download Package

```http
GET /package/foo/0.1.0 HTTP/1.1
Host: registry.diamond.js.org
```

> The above request returns a gzipped tarball (`.tar.gz`)

This endpoint gets package contents.

### HTTP Request

`GET /package/:name/:version`

### URL Parameters
| Key | Type | Description |
|-----|------|-------------|
| name | string | The name of the package you want to download |
| version | [SemVer](http://semver.org/) &#124; string | The version or tag that you want to download |

### Reponse Format

A gzipped tarbal (`.tar.gz`) file is returned.