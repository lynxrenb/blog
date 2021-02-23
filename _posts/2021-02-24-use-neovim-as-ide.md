---
layout: post
title: Using Neovim as C++ IDE
categories:
    - cpp
    - neovim
tags: 
    - nvim
    - cpp
---

![Neovim Cpp](https://raw.githubusercontent.com/lynxrenb/files/master/nvim_config.png)

Today, I will describe how to turn Neovim into a powerful IDE for C++ projects.

### Prerequirements

First of all you have to install plugins like language server support,
code completion, highlighting.
Or install this [config](https://github.com/lynxrenb/nvim#neovim-config),
it will take care of all the necessary plugins.

You should also have following tools.

* Clang
* Cmake

### Project Structure

Your project root should contain _.clang-format_, _.clang-tidy_ and _compile_commands.json_
for following tools. Use this [starter project](https://github.com/lynxrenb/cpp_starter_project)
if you are new to these files.

* **Clang-format**

  clang-format is a tool to automatically format C/C++/Objective-C code,
so that developers don't need to worry about style issues during code reviews.

* **Clang-tidy**

  clang-tidy is a clang-based C++ “linter” tool. Its purpose is to provide an
extensible framework for diagnosing and fixing typical programming errors,
like style violations, interface misuse, or bugs that can be deduced via static analysis.

* **Generate _compile_commands.json_**

  This document describes a format for specifying how to replay single compilations
independently of the build system.

  Currently CMake (since 2.8.5) supports generation of compilation databases
for Unix Makefile builds (Ninja builds in the works) with the option
_CMAKE_EXPORT_COMPILE_COMMANDS_.

* ##### Example

```json
[
  { "directory": "/home/user/cpp",
    "command": "/usr/bin/c++ main.cpp -o main",
    "file": "main.cpp" 
  }
]
```

## Screen

![neovim compare](https://raw.githubusercontent.com/lynxrenb/files/master/nvim_compare.png)

Plugins included (left) vs default Neovim (right).
