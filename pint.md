# Laravel Pint

- [Introduction](#introduction)
- [Installation](#installation)
- [Running Pint](#running-pint)
- [Configuring Pint](#configuring-pint)
    - [Presets](#presets)
        - [Laravel Preset](#laravel-preset)
    - [Rules](#rules)
    - [Excluding Files / Folders](#excluding-files-or-folders)

<a name="introduction"></a>
## Introduction

[Laravel Pint](https://github.com/laravel/pint) is an opinionated PHP code style fixer for minimalists. Pint is built on top of PHP-CS-Fixer and makes it simple to ensure that your code style stays clean and consistent.

Pint is automatically installed with all new Laravel applications so you may start using it immediately. By default, Pint does not require any configuration and will fix code style issues in your code by following the opinionated coding style of Laravel.

<a name="installation"></a>
## Installation

Pint is included in recent releases of the Laravel framework, so installation is typically unnecessary. However, for older applications, you may install Laravel Pint via Composer:

```shell
composer require laravel/pint --dev
```

<a name="running-pint"></a>
## Running Pint

You can instruct Pint to fix code style issues by invoking the `pint` binary that is available in your project's `vendor/bin` directory:

```shell
./vendor/bin/pint
```

You may also run Pint on specific files or directories:

```shell
./vendor/bin/pint app/Models

./vendor/bin/pint app/Models/User.php
```

Pint will display a thorough list of all of the files that it updates. You can view even more detail about Pint's changes by providing the `-v` option when invoking Pint:

```shell
./vendor/bin/pint -v
```

If you would like Pint to simply inspect your code for style errors without actually changing the files, you may use the `--test` option:

```shell
./vendor/bin/pint --test
```

If you would like Pint to only modify the files that have uncommitted changes according to Git, you may use the `--dirty` option:

```shell
./vendor/bin/pint --dirty
```

<a name="configuring-pint"></a>
## Configuring Pint

As previously mentioned, Pint does not require any configuration. However, if you wish to customize the presets, rules, or inspected folders, you may do so by creating a `pint.json` file in your project's root directory:

```json
{
    "preset": "laravel"
}
```

In addition, if you wish to use a `pint.json` from a specific directory, you may provide the `--config` option when invoking Pint:

```shell
pint --config vendor/my-company/coding-style/pint.json
```

<a name="presets"></a>
### Presets

Presets defines a set of rules that can be used to fix code style issues in your code. By default, Pint uses the `laravel` preset, which fixes issues by following the opinionated coding style of Laravel. However, you may specify a different preset by providing the `--preset` option to Pint:

```shell
pint --preset psr12
```

If you wish, you may also set the preset in your project's `pint.json` file:

```json
{
    "preset": "psr12"
}
```

Pint's currently supported presets are: `laravel`, `psr12`, and `symfony`.

<a name="laravel-preset"></a>
### Laravel preset

The Laravel preset differs from PSR-12 in the following key ways.

1. Array Indentation: The Laravel preset enforces array indentation.
2. Array Syntax: The Laravel preset enforces the short array syntax.
3. Single Quote: The Laravel preset enforces single quotes for string literals.
4. PHPDoc alignment: The Laravel preset enforces 2 spaces after @param and type definitions.
5. Control Structure Braces: The Laravel preset allows control braces to be on the same line as the control structure.
6. Curly Braces Position: The Laravel preset allows for opening curly braces for control structures and classes can be on the same line or the next line.
7. Function Declaration: The Laravel preset does not enforce a space between the function keyword and the opening parenthesis of the parameter list.
8. Line Ending: The Laravel preset does not enforce specific line endings. PSR-12 enforces Linux line endings (LF).
9. Whitespace After Comma in Array: The Laravel preset does not enforce whitespace after commas in an array

<a name="rules"></a>
### Rules

Rules are style guidelines that Pint will use to fix code style issues in your code. As mentioned above, presets are predefined groups of rules that should be perfect for most PHP projects, so you typically will not need to worry about the individual rules they contain.

However, if you wish, you may enable or disable specific rules in your `pint.json` file:

```json
{
    "preset": "laravel",
    "rules": {
        "simplified_null_return": true,
        "braces": false,
        "new_with_braces": {
            "anonymous_class": false,
            "named_class": false
        }
    }
}
```

Pint is built on top of [PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer). Therefore, you may use any of its rules to fix code style issues in your project: [PHP-CS-Fixer Configurator](https://mlocati.github.io/php-cs-fixer-configurator).

<a name="excluding-files-or-folders"></a>
### Excluding Files / Folders

By default, Pint will inspect all `.php` files in your project except those in the `vendor` directory. If you wish to exclude more folders, you may do so using the `exclude` configuration option:

```json
{
    "exclude": [
        "my-specific/folder"
    ]
}
```

If you wish to exclude all files that contain a given name pattern, you may do so using the `notName` configuration option:

```json
{
    "notName": [
        "*-my-file.php"
    ]
}
```

If you would like to exclude a file by providing an exact path to the file, you may do so using the `notPath` configuration option:

```json
{
    "notPath": [
        "path/to/excluded-file.php"
    ]
}
```
