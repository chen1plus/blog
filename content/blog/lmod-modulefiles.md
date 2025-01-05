+++
title = "How to Write Lmod Modulefiles"
date  = "2025-01-02"
description = "A concise guide to creating Lmod modulefiles to manage software environments in high-performance computing (HPC) systems."

[taxonomies]
tags = ["HPC", "Lmod", "modulefiles"]
+++

Lmod is a modern environment module system widely used in HPC to manage software environments. Writing custom modulefiles allows users to easily load and configure software.

# Basics

Modulefiles are Lua scripts that define the environment variables required to use a software package. You should learn the basic syntax of Lua first.

```lua
-- This is a comment.

--[[
This is a multi-line comment.
This is a multi-line comment.
--]]

-- This is a local variable.
local x = 10

-- You can concatenate strings. Ex:
local str = "Hello, " .. "World!"

-- This is a multi-line string.
local poem = [[
S’io credesse che mia risposta fosse
A persona che mai tornasse al mondo,
Questa fiamma staria senza piu scosse.
Ma percioche giammai di questo fondo
Non torno vivo alcun, s’i’odo il vero,
Senza tema d’infamia ti rispondo.
]]
```

Lmod provides several functions to manage environment variables. The most commonly used functions are:

- `setenv`: sets an environment variable.
- `prepend_path`: adds a path to the beginning of an environment variable.

There are also functions to provide information about the module:

- `whatis`: provides a brief description.
- `help`: provides detailed information.

## Example

```lua
local base = "/path/to/software"

setenv("SOFTWARE_HOME", base)

prepend_path("PATH", pathJoin(base, "bin"))
prepend_path("LD_LIBRARY_PATH", pathJoin(base, "lib"))

-- info
whatis("Name: software_name")
whatis("Version: x.x")
whatis("Description: Brief description of the software")

help([[
This modulefile sets up the environment for software_name version x.x.
]])
```
