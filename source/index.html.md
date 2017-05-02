---
title: diamond Registry Docs

language_tabs:
  - http

toc_footers:
  - <a href='https://diamond.js.org'>Home</a>

includes:
  - user
  - package

search: true
---

# Introduction

```text
                 ___====-_  _-====___
           _--^^^#####//      \\#####^^^--_
        _-^##########// (    ) \\##########^-_
       -############//  |\^^/|  \\############-
     _/############//   (@::@)   \\############\_
    /#############((     \\//     ))#############\
   -###############\\    (oo)    //###############-
  -#################\\  / VV \  //#################-
 -###################\\/      \//###################-
_#/|##########/\######(   /\   )######/\##########|\#_
|/ |#/\#/\#/\/  \#/\##\  |  |  /##/\#/  \/\#/\#/\#| \|
`  |/  V  V  `   V  \#\| |  | |/#/  V   '  V  V  \|  '
   `   `  `      `   / | |  | | \   '      '  '   '
                    (  | |  | |  )
                   __\ | |  | | /__
                  (vvv(VVV)(VVV)vvv)
```

<aside class="warning">The registry is not yet active.</aside>

Welcome to the diamond registry API! You can use the diamond registry to get and manage packages for diamond.

API Root: `registry.diamond.js.org`

All requests should use SSL.

## Versions

All requests should prefix requests with a version. E.g. `registry.diamond.js.org/v1/foo`

| Name | Out of Service? |
|------|-----------------|
| v1 | No |

# Authentication

> Your `Authorization` header should look like this:

```text
Authorization: Basic eW91IHRvb2sgdGhlIHRpbWUgdG8gcmVhZCB0aGlzPyBnZw==
```

Authentication is done via [HTTP Basic](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Basic_authentication_scheme) so you should always use SSL.

