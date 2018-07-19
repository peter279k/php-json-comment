## adhocore/json-comment

[![Latest Version](https://img.shields.io/github/release/adhocore/json-comment.svg?style=flat-square)](https://github.com/adhocore/json-comment/releases)
[![Travis Build](https://img.shields.io/travis/adhocore/json-comment/master.svg?style=flat-square)](https://travis-ci.org/adhocore/json-comment?branch=master)
[![Scrutinizer CI](https://img.shields.io/scrutinizer/g/adhocore/json-comment.svg?style=flat-square)](https://scrutinizer-ci.com/g/adhocore/json-comment/?branch=master)
[![Codecov branch](https://img.shields.io/codecov/c/github/adhocore/json-comment/master.svg?style=flat-square)](https://codecov.io/gh/adhocore/json-comment)
[![StyleCI](https://styleci.io/repos/100117199/shield)](https://styleci.io/repos/100117199)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)


- Lightweight JSON comment stripper library for PHP.
- Makes possible to have comment in any form of JSON data.
- Supported comments: single line `// comment` or multi line `/* comment */`.

## Installation
```bash
composer require adhocore/json-comment
```

## Usage
```php
use Ahc\Json\Comment;

// The JSON string!
$someJsonText = '{"a":1,
"b":2,// comment
"c":3 /* inline comment */,
// comment
"d":/* also a comment */"d",
/* creepy comment*/"e":2.3,
/* multi line
comment */
"f":"f1"}';

// OR
$someJsonText = file_get_contents('...');

// Strip only!
(new Comment)->strip($someJsonText);

// Strip and decode!
(new Comment)->decode($someJsonText);

// You can pass args like in `json_decode`
(new Comment)->decode($someJsonText, $assoc = true, $depth = 512, $options = JSON_BIGINT_AS_STRING);

// Or you can use static alias of decode:
Comment::parse($json, true);
```
