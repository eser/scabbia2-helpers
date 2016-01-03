# Scabbia2 Helpers Component

[This component](https://github.com/eserozvataf/scabbia2-helpers) is the swiss knife for rest of the scabbia2 components. Includes most commonly used helper methods filed under `Arrays`, `Date`, `FileSystem`, `Html`, `Runtime` and `String` static classes.

[![Build Status](https://travis-ci.org/eserozvataf/scabbia2-helpers.png?branch=master)](https://travis-ci.org/eserozvataf/scabbia2-helpers)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/eserozvataf/scabbia2-helpers/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/eserozvataf/scabbia2-helpers/?branch=master)
[![Total Downloads](https://poser.pugx.org/eserozvataf/scabbia2-helpers/downloads.png)](https://packagist.org/packages/eserozvataf/scabbia2-helpers)
[![Latest Stable Version](https://poser.pugx.org/eserozvataf/scabbia2-helpers/v/stable)](https://packagist.org/packages/eserozvataf/scabbia2-helpers)
[![Latest Unstable Version](https://poser.pugx.org/eserozvataf/scabbia2-helpers/v/unstable)](https://packagist.org/packages/eserozvataf/scabbia2-helpers)
[![Documentation Status](https://readthedocs.org/projects/scabbia2-documentation/badge/?version=latest)](https://readthedocs.org/projects/scabbia2-documentation)

## Usage

### Arrays

```php
use Scabbia\Helpers\Arrays;

$output = Arrays::flat(['a', ['b', 'c']]);
// $output == ['a', 'b', 'c']

$output = Arrays::getFirst(['a', 'b']);
// $output == 'a'

$output = Arrays::get(['a' => '1', 'b' => '2'], 'b');
// $output == '2'

$output = Arrays::getArray(['a' => '1', 'b' => '2', 'c' => '3'], 'a', 'c', 'd');
// $output == ['a' => '1', 'c' => '3', 'd' => null];

$output = Arrays::getPath(['a' => ['b' => ['c' => 5]]], 'a/b/c');
// $output == 5

$output = Arrays::getArrayPath(['a' => ['b' => ['c' => 5, 'd' => 6]]], 'a/b/c', 'a/b/d', 'a/b/e');
// $output == ['a/b/c' => 5, 'a/b/d' => 6, 'a/b/e' => null];

$output = Arrays::getRandom(['a', 'b', 'c']);
// $output == 'c'

$output = Arrays::range(1, 5);
// $output == [1, 2, 3, 4, 5]

$output = Arrays::sortByKey([
    ['i' => 5],
    ['i' => 2],
    ['i' => 4]
], 'i');
// $output == [['i' => 2], ['i' => 4], ['i' => 5]]

$output = Arrays::categorize([
    ['t' => 'a', 'i' => 5],
    ['t' => 'b', 'i' => 2],
    ['t' => 'a', 'i' => 4]
], 't');
// $output == [
//     'a' => [['t' => 'a', 'i' => 5], ['t' => 'a', 'i' => 4]],
//     'b' => [['t' => 'b', 'i' => 2]],
// ]

$output = Arrays::assignKeys([
    ['i' => 5],
    ['i' => 2],
    ['i' => 4]
], 'i');
// $output == [5 => ['i' => 5], 2 => ['i' => 2], 4 => ['i' => 4]]

$output = Arrays::column([
    ['i' => 5],
    ['i' => 2],
    ['i' => 4]
], 'i');
// $output == [5, 2, 4]

$output = Arrays::columns([
    ['i' => 5, 'j' => 6, 'k' => 7],
    ['i' => 2, 'j' => 3, 'k' => 4],
    ['i' => 4, 'j' => 5, 'k' => 6]
], 'i', 'k');
// $output == [
//     ['i' => 5, 'k' => 7],
//     ['i' => 2, 'k' => 4],
//     ['i' => 4, 'k' => 6]
// ]

$output = Arrays::getRow([
    ['i' => 5, 'j' => 6, 'k' => 7],
    ['i' => 2, 'j' => 3, 'k' => 4],
    ['i' => 5, 'j' => 5, 'k' => 6]
], 'i', 5);
// $output == ['i' => 5, 'j' => 6, 'k' => 7]

$output = Arrays::getRowKey([
    'a' => ['i' => 5, 'j' => 6, 'k' => 7],
    'b' => ['i' => 2, 'j' => 3, 'k' => 4],
    'c' => ['i' => 5, 'j' => 5, 'k' => 6]
], 'i', 5);
// $output == 'a'

$output = Arrays::getRows([
    ['i' => 5, 'j' => 6, 'k' => 7],
    ['i' => 2, 'j' => 3, 'k' => 4],
    ['i' => 5, 'j' => 5, 'k' => 6]
], 'i', 5);
// $output == [
//     ['i' => 5, 'j' => 6, 'k' => 7],
//     ['i' => 5, 'j' => 5, 'k' => 6]
// ]

$output = Arrays::getRowsBut([
    ['i' => 5, 'j' => 6, 'k' => 7],
    ['i' => 2, 'j' => 3, 'k' => 4],
    ['i' => 5, 'j' => 5, 'k' => 6]
], 'i', 5);
// $output == [
//     ['i' => 2, 'j' => 3, 'k' => 4]
// ]

$output = Arrays::sortByPriority([
    'second' => 221,
    'forth' => 444,
    'third' => 727,
    'first' => 878
], ['first', 'second']);
// $output == ['first' => 878, 'second' => 221, 'forth' => 444, 'third' => 727]
```

## Links
- [List of All Scabbia2 Components](https://github.com/eserozvataf/scabbia2)
- [Documentation](https://readthedocs.org/projects/scabbia2-documentation)
- [Twitter](https://twitter.com/eserozvataf)
- [Contributor List](contributors.md)
- [License Information](LICENSE)


## Contributing
It is publicly open for any contribution. Bugfixes, new features and extra modules are welcome. All contributions should be filed on the [eserozvataf/scabbia2-helpers](https://github.com/eserozvataf/scabbia2-helpers) repository.

* To contribute to code: Fork the repo, push your changes to your fork, and submit a pull request.
* To report a bug: If something does not work, please report it using GitHub issues.
* To support: [![Donate](https://img.shields.io/gratipay/eserozvataf.svg)](https://gratipay.com/eserozvataf/)
