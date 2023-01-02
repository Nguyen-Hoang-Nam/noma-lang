# NOMA Language Specification

The specification for consistent programming language aims to erase the new overhead syntaxes.

## 1 Syntax

### 1.1 Object

Object is term to describe things that relative with syntax `{}`. There are 2 relative positions for syntax `{}`.

#### 1.1.1 Metadata (Head position)

Metadata is in the Head of syntax `{}`, this is a special part of Object because it need parser to create a special case to match it. Because of this reason, there are by default have limit of Metadata of each Object.

##### 1.1.1.1 `__NAME__`

There are 2 ways to access data inside Object by assigning object with a variable or define a name.

Ex: `name {}`

##### 1.1.1.2 `__PARAMS__`

In case of Function, to get the parameters Object use `__PARAMS__`.

Ex: `(param_1, param_2) {}`

#### 1.1.2 Content (Body position)

Content part contain data and logic for its Object. To do these things, Content need some special syntax.

##### 1.1.2.1 `public` syntax

Inside Content everything is private, so to get its data this variables must have `public` syntax before it. Because of immutation, when outside of Object get `public` data, they only get data at the time public.

Ex:

```text
example_pubic {
  var_1 = 1
  var_2 = 2
  public var_3 = var_1 + var_2
  
  var_3 = 4
}

IO.print(example_pubic.var_3) // 3
```

Important thing, there are no ways to assign data inside Object even public variables as Object is immutable.

##### 1.1.2.2 Return

To deal with logic, Object always return the last line of its Content.

Ex:

```text
add(param_1, param_2) {
  param_1 + param_2
}

add(1, 1) |> IO.print() // 2
```

### 1.2 Operator

Noma keep most of operators from other languages. `+, -, *, /, >, >=, <, <=, =, ==, >>, <<, !, ||, &&, |>`

## 2 Structure

To make project structure more clear, there are some conventions.

### 2.1 Project

The project is a set of Noma language files.

### 2.2 File

The file is a system file that contain one or multiple modules.

### 2.3 Module

Module define a Object that does not inside any other Object. By convention, name of Module shoud be Pascal case.

Ex:

```text
// module_name.noma file
ModuleName {
  
}
```

### 2.4 Function

Function is a Object inside Module. By convention, name of function shoud be snake case.

Ex:

```text
// module_name.noma file
ModuleName {
  public function_name(param_1, param_2) {}
}

// other.noma file
ModuleName.function_name(1, 1)
```
