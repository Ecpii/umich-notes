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
|**Relocation table**|list of instructions and data words that must be updated if things are moved in memory|

### Symbol Table
This keeps track of
- global variables and exported functions
- unresolved variables / functions
- static variables (data)
each entry contains:
|Label|Type (Text/Data/Unknown)|Address (Section and Offset)|
|---|---|---|

### Relocation Table
When linking files, sections in the code move around - the **relocation table**  tracks what instructions need to be update:
- Calls to functions (**both** global and local)
- References to anything in the Data section
each entry contains:
|Address of Instruction|Instruction/Directive Type|Referenced Symbol|
|---|---|---|

## Linker Behavior
A linker stiches object files into a single file.
- first, take the text segment from each object and put them together
- next, take the data segment from each object and put them together, put this at the end of the content


# Memory Mapping
There are four different spaces of memory in a computer program:
- **Text** - direct instructions in the program (function calls, etc)
- **Data** - static and global data/variables
- **Heap** - dynamic memory
- **Stack** - local variables for functions, includes parameters

