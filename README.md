# `random`: functions module for [shellfire]

This module provides an immature framework for accessing random values from shell script. It employs a number of fallback strategies, each of which sources a less random, less acceptable source. There are no known users, and you should consider this code alpha quality, subject to change, etc.

## Compatibility

* Tag [`release_2015.0117.1750-1`](https://github.com/shellfire-dev/version/releases/tag/release_2015.0117.1750-1) is compatible with [shellfire] release [`release_2015.0117.1750-1`](https://github.com/shellfire-dev/shellfire/releases/tag/release_2015.0117.1750-1).

## Overview

For example, to generate a random number between 0 and 255:-

```bash
randomValue="$(random_generateBetween0To255)"
```

## Importing

To import this module, add a git submodule to your repository. From the root of your git repository in the terminal, type:-
```bash
mkdir -p lib/shellfire
cd lib/shellfire
git submodule add "https://github.com/shellfire-dev/random.git"
cd -
git submodule init --update
```

You may need to change the url `https://github.com/shellfire-dev/random.git"` above if using a fork.

You will also need to add paths - include the module [paths.d].


## Namespace `random`

### To use in code

If calling from another [shellfire] module, add to your shell code the line
```bash
core_usesIn random
```
in the global scope (ie outside of any functions). A good convention is to put it above any function that depends on functions in this module. If using it directly in a program, put this line _inside_ the `_program()` function:-

```bash
_program()
{
	core_usesIn random
	…
}
```

### Functions

***
#### `random_generateBetween0To255()`
Takes no parameters.

Writes a number between 0 and 255 inclusive to standard out, using the best available source of randomness.

***
#### `random_generateBetween0AndModulus()`
|Parameter|Value|Optional|
|---------|-----|--------|
|`modulus`|Modulus, must be between 1 and 255 (not validated)|_No_|

Writes a number between 0 and `modulus` to standard out, using randomness from `random_generateBetween0To255()`.

***
#### `random_characterForEncodingLowerCaseOnly()`
Takes no parameters.

Writes a lower case ASCII character or digit to standard out, using randomness from `random_generateBetween0To255()`.

***
#### `random_characterForEncodingLettersAndNumbers()`
Takes no parameters.

Writes a lower or upper case ASCII character or digit to standard out, using randomness from `random_generateBetween0To255()`.

***
#### `random_characterForEncodingBase64Like()`
Takes no parameters.

Writes an ASCII character suitable for use in Base64 encoding to standard out, using randomness from `random_generateBetween0To255()`. Highly experimental. Do not rely on this function being present.






[swaddle]: https://github.com/raphaelcohn/swaddle "Swaddle homepage"
[shellfire]: https://github.com/shellfire-dev "shellfire homepage"
[core]: https://github.com/shellfire-dev/core "shellfire core module homepage"
[paths.d]: https://github.com/shellfire-dev/paths.d "paths.d shellfire module homepage"
