# XORLang

## Description

In computer science we attempt to control machines by introducing determinism.
In nature we see some systems change their state redefining themselves as the system evolves.
XORLang is an attempt to complexify code by using simple logic and statement dependency.
This is a very experimental language and has a far way to go, it may classify as an Esolang.

## Requirements

To install, Python2 and Antlr4 is required to be installed on your machine.
After you've installed Antlr4 on your system, install the python requirement for [Antlr4](https://github.com/antlr/antlr4) & [pwntools](https://github.com/Gallopsled/pwntools):

```
pip install -r requirements.txt
```

## Usage

To run a simple program, cd to `lib` and run:

```
$ ./xorlang examples/simple2.xor
> '{'
```

## Technical Details

- The global state starts as '\0'
- Each instruction is considered dependant, relying on previous XOR operations
- A single register is used within the life of a running program, `X`
- The `X` register will keep track of the current XOR state
- Any values used within the program will update the `X` register when executed
- Granularity may be applied to update `X` on every statement or every byte (see `M`)
- The global state value of `X` may be cleared, but should be done sparingly,
  this may be done by executing the statement: `XX`
- The pipe character is used as a separator `|`

## Example Syntax

```
| X 5
| X 'AAAA'
| X [1,2,3,4]
| X 'Hello World!'
| print

> '\r#+,*f\x10/7*#a'
```

## Alternative Syntax

```
| < 5
| < 'AAAA'
| < [1,2,3,4]
| < 'Hello World!'
| print

> '\r#+,*f\x10/7*#a'
```

## Operators

- `X`,`<` : Update the current state with any value, takes one argument
- `M`     : Mode of `X` operation, flags may be passed into value
- `print` : Print the current state of `X`, or any argument passed in

## Mode Flags

- `S` (statement-level state change)
- `C` (character-level state change)

