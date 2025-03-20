---
title: Setting Things Up
summary: Core settings for new users!
author: Dusk(Wyn)
date : 2025-10-22
---
# Creating a Project
First things first, a project must be created to begin your journey.

A project may be created through:
`Maven new <project name>`

For this documentation, the project will be `Example`

After a project has been created, there will be several files present:
```
.
├── Package.lock
├── Package.toml
└── src
    └── Example.mvn
```

`Package.lock` is a file meant to be managed by Maven so it can be ignored.

`Package.toml` will look like this:
```
[project]
name = "Example"
version = "0.1.0"
type = "static"
authors = []

[outputs]
Example = "target_file_format"
#eg. hello_world =  exec

[targets]
targets = ["native"]

[emissions]
#eg. hello_world =  ["object"]

[artifacts]
```

# Breaking it down
### Project
```
[project]
name = "Example"
version = "0.1.0"
type = "static"
authors = []
```
Here you can specify the project name, it's current version and type.

Type refers to whether you are using Maven's **static** typed version or Maven's **dynamic** typed version

Authors can be structured as such:

`authors = ["me", "myself", "& i"]`
### Outputs
```
[outputs]
Example = "target_file_format"
#eg. hello_world =  exec
```
This tells Maven what format you want your file to be, some common formats include:

- exec: Executable native of the platform

- deck: Maven's library file format

- static_lib: A **.a** archive of the produced **.o**

- dylib: A native dynamic library
### Targets
```
[targets]
targets = ["native"]
```
A target refers to an operating system you are targeting, `native` by default choses your operating system.
An example of another target for Windows for example would be: `x86_64-pc-windows-msvc`
Another example for Apple iOS would be: `apple-ios-arm64`

(note: Maven does not support out of the box cross compilation and additional settings may have to be configured)
### Emissions
```
[emissions]
#eg. hello_world =  ["object"]
```
Emissions refer to byproducts of the compilation process you wish to keep, current supported emissions are:

- Object: **.o** file

- llvm_ir: **.ir** file representing LLVM's immediate representation
### Artifacts
```
[artifacts]
```
Artifacts refer to packages that your project depends on, at the start there are no artifacts to depend on!