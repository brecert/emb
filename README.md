# Emb

> A programming language idea that I have

_I'm currently making up a lot of the ideas as I go, so the examples may be inconsistent (although I've tried to keep them consistent)_

Currently it draws inspiration from

- powershell for the idea of functions being valid commands, and complex parts of the language still just being shell
- elixir for how elegant syntax sugar can be
- rust for api concepts and some type concepts
- dyon for some of the "weirder" ideas it's introduced

In it's current form, it'd be unfeasable to realistically implement

Things I want for a language like this

- able to be compiled/executed with the command structure intact and helper options added
  see [minecraft.expected.slang](./examples/minecraft.expected.slang) for what I'd want that to look like
- advanced types, just because it's more dynamic/scripting does not mean types should be avoided
  - instead types will be mostly inferred
  - really only
    - new types
    - input types
      should be required
- an alternative syntax, I want to find a nice alternative to bash/powershell/scripting
  - simple and clean
  - just enough symbols for identification
  - clear separation between different syntax layers (for example, between an object and a type)
  - somewhat user definable syntax
  - pattern based syntax
- ease of use
- an easy to use "batteries included" standard library, but still explicit enough to not use that standard library when not needed

## Type system

The type syntax layer should be indicated with `<type expression>`

Examples:

```rs
type Username <string>
type <infer A, B> Either <enum { A: A, B: B }>
type <infer T> Maybe <enum { Some: T, None }>

// paths aren't bound by `/`, and can be represented/used in multiple forms
use std:unwrap

// _ refers to the current self, although this may just be changed to self in the future
// {} is used for interpolating variables, although some enclosure types are automatically interpolated like strings

impl <unwrap> for <Maybe>
  def unwrap <self>
    match {self} {
      Maybe:Some:<T> => T,
      Maybe:None => panic "Unable to unwrap Maybe"
    }
```