# Linking
When trying to compile files that rely on other files, it is normally impossible because offsets may conflict. Linking is the process of making "partially" compiled and assembled versions of programs, then combining those intermediate files into a complete program. The intermediate file here is also called an **object file**.
In linking, we need to keep track of
- the assembled machine code
- list of instructions that need to be updated once addresses are resolved
- list of symbols to cross reference

## Object Files
The object file includes the machine code that will go into the final executable, and other information that will help with linking. An object file has the following format:
|Section|Description|
|---|---|
|**Header**|keeps track of size of each section|
|**Text**|(unfinished) machine code|
|**Data**| initialized global and static locals (like `.fill`s)|
|**Symbol table**|lists all the symbols that could possibly be used outside this file|
|**Reloc table**|list of instructions and data words that must be updated if things are moved in memory|
## Linker Behavior
A linker stiches object files into a single file.
- first, take the text segment from each object and put them together
- next, take the data segment from each object and put them together, put this at the end of the content
- 
