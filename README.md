# dice

A portable bash dice roller.

## Usage

```
dice <expr> [<expr> ...]
```

## Expressions

| Syntax | Description | Examples |
|--------|-------------|---------|
| `dM` | Roll one M-sided die | `d6`, `d20` |
| `NdM` | Roll N M-sided dice and sum | `2d6`, `3d8` |
| `N` | Constant | `4`, `10` |
| `A + B` | Sum expressions | `d6 + 4`, `2d8 + 1d4` |

Expressions can be combined freely:

```
$ dice 2d6 + d4 + 3
2d6 + d4 + 3 => 14
```

## Multiple results

Space- or comma-separated expressions are rolled independently and displayed as a list:

```
$ dice d6 d12
d6 d12 => 3, 11

$ dice d6, d12
d6, d12 => 3, 11
```

## Max / Min functions

`max:A, B, ...:` returns the highest, `min:A, B, ...:` returns the lowest, of any number of expressions:

```
$ dice max:d6,4:
max:d6,4: => 4

$ dice min:d6,4:
min:d6,4: => 2

$ dice max:1d4+1d8,1:
max:1d4+1d8,1: => 7

$ dice max:1d6, 1d6+1, 4:
max:1d6, 1d6+1, 4: => 5

$ dice max:d6,4: + d4
max:d6,4: + d4 => 8

$ dice min:max:d4,d6:,3:
min:max:d4,d6:,3: => 3
```

## Installation

Copy `dice` to somewhere on your `PATH`, e.g.:

```
cp dice /usr/local/bin/dice
```
