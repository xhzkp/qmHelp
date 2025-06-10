# Quick Macros Quick Start Guide

This is a concise but comprehensive quick start tutorial for **Quick Macros (QM)**. It introduces the core concepts, operations, and most important commands, designed for beginners and as a handy reference for experienced users.

---

## Table of Contents

- [What is a Macro](#what-is-a-macro)
- [How Quick Macros Works](#how-quick-macros-works)
- [Quick Macros Main Window](#quick-macros-main-window)
- [Creating Macros, Menus, or Toolbars](#creating-macros-menus-or-toolbars)
- [Adding Macro Commands](#adding-macro-commands)
- [Recording Operations](#recording-operations)
- [Menus and Toolbar Buttons](#menus-and-toolbar-buttons)
- [How to Launch Macros](#how-to-launch-macros)
- [Macro Running Status](#macro-running-status)
- [How to End a Running Macro](#how-to-end-a-running-macro)
- [Using Variables and Strings](#using-variables-and-strings)
- [Loops and Conditionals](#loops-and-conditionals)
- [Top 20 Most Used Commands](#top-20-most-used-commands)

---

## What is a Macro

A macro is a list of commands that are executed in sequence when the macro runs. These commands can perform the same actions as you can do manually: type text, click menus, run files, and more.  
You can assign a **trigger** (such as a hotkey) to a macro, add it to a toolbar, or launch it by other means. Instead of repeating the same steps manually, you can run the macro with a single click or keystroke.

---

## How Quick Macros Works

In the **Quick Macros window**, you can create macros and other items (functions, toolbars, menus, etc.). Each task you want to automate should have its own macro. Macros can be assigned triggers, e.g., hotkeys, mouse actions, window events.

While Quick Macros is running, it monitors for these triggers. When a trigger event occurs, Quick Macros executes the assigned macro. QM also manages your custom toolbars and menus.

---

## Quick Macros Main Window

- **Top**: Menu and toolbars.
- **Left**: List of QM items (macros, functions, menus, toolbars, etc.).
- **Middle**: Code editor. Here you edit the commands of the selected item.
- **Bottom**: Output area (shows errors and messages), Find, Tips, Status bar.

---

## Creating Macros, Menus, or Toolbars

- To create a new macro, click the **New Macro** button on the toolbar and type a name in the field that appears.
- To create other item types (function, toolbar, etc.), use the popup menu beside the New Macro button.

---

## Adding Macro Commands

- Macros are stored as plain text, usually with one command per line.
- You can add commands using dialogs from the code toolbar, but not all commands have dialog boxes—some must be typed manually.
- You can search for commands and dialogs using the **Find help, functions, tools** field above the code editor.
- The easiest way to add keyboard and mouse commands is to **record** them.

---

## Recording Operations

- You can record keyboard and mouse actions to create a macro, or just part of it.
- To start recording, click the **Record** button on the toolbar or press `Ctrl+Shift+Alt+R`.
- After finishing, click **Insert** in the QM Recording dialog.
- Recorded macros usually require review and editing, e.g., adding delays or changing window names.
- When recording, prefer using keyboard shortcuts over mouse actions for more robust macros.

---

## Menus and Toolbar Buttons

Menu text and toolbars are essentially lists of commands, each line creating a menu item or toolbar button. Each line uses the format: `Label : Command`

**Example:**
```qm
Macro18 : mac "Macro18"
Notepad : run "$system$\notepad.exe"
-
Email : key "my@ema.il" * text.ico
Login : key "abcd"; key T; key "1234"; key Y * text.ico
```
- To quickly add a macro, drag it from the item list to the menu/toolbar text.
- To add a file, use the **Run File** dialog or drag it from Explorer.
- Use `-` or `|` to add a separator.
- Use the **Icons** dialog to add icons to menu items or buttons.

---

## How to Launch Macros

You can launch macros in several ways:
- Run button on the QM toolbar
- Hotkey, mouse, window, or other trigger (set in Properties)
- Place macro in a custom menu or toolbar and launch from there
- Schedule to run at a certain time
- Create a desktop shortcut (set in Properties)
- Launch from another macro using the `mac` command
- Use autotext (text replacement triggers)

Menus, toolbars, and functions can be launched in the same ways.

---

## Macro Running Status

When a macro is running, the QM tray icon turns red.  
When other QM items (functions, menus, etc.) are running, the tray icon does not change.  
You can see all running items in the **Running items** pane in the QM window or in the **Threads** dialog in the QM tray menu.

---

## How to End a Running Macro

- When a macro is running, press the **Pause** key (can be changed in Options).
- If input is blocked (due to `BlockInput`), first press `Ctrl+Alt+Delete`.
- For functions or macros with 'Run simultaneously' option, use the **Running items** pane or Threads dialog to end them.
- You can also add custom code in your macro to allow it to be stopped, e.g.:
    ```qm
    rep
        ifk(F12) ret ;; end if F12 is pressed
        ...
    ```

---

## Using Variables and Strings

You can use variables almost everywhere in QM code.  
- Use `int` for integer values, `double` for floating-point, `str` for text.

**Example (without variables):**
```qm
lef 100 200 "Notepad"
```

**Example (with variables):**
```qm
str s="Notepad" ;; declare str variable s, assign "Notepad"
int x y         ;; declare int variables x and y
x=100
y=x*2
lef x y s
```

To share a variable between macros, declare it with `+`:
```qm
int+ global_var
```

**Strings** must be enclosed in double quotes. Use `''` to represent a quote and `[]` for a newline.
```qm
out "This is[]a multiline string[]with ''double quotes''."
```

You can also declare multiline strings:
```qm
str s=
 This is
 a multiline string
 with "double quotes".
out s
```

---

## Loops and Conditionals

**Loop (repeat commands):**
```qm
rep 10
    lef 100 200
    key Y
```

**Conditional execution:**
```qm
if i<5
    out "variable i < 5"
    i+1
else
    out "variable i >= 5"
```

---

## Top 20 Most Used Commands

Here are the 20 most important QM commands, with descriptions and examples:

| Command      | Purpose & Example |
|--------------|------------------|
| **lef, rig** | Mouse click<br> `lef 100 200 ;; left click at 100x200`<br>`lef 90 40 "Notepad"` |
| **key**      | Keyboard actions<br> `key "Australia"`<br>`key F12`<br>`key Cv ;; Ctrl+V` |
| **paste**    | Paste text<br> `paste "New Zealand"`<br>`paste s` |
| **out**      | Output to QM window<br> `out "I am here"`<br>`out i` |
| **mes**      | Show message box<br> `mes "Important information"`<br>`if(mes("Continue?" "" "YN")='N') ret` |
| **run**      | Run file, open document or URL<br> `run "C:\WINDOWS\system32\notepad.exe"`<br>`run "http://www.quickmacros.com"` |
| **act**      | Activate window<br> `act "Notepad"` |
| **win**      | Find window and get handle<br> `int hwnd=win("Internet Explorer" "IEFrame")`<br>`act hwnd` |
| **wait**     | Wait/delay<br> `wait 5 ;; wait 5 seconds`<br>`wait 30 "Internet Explorer"` |
| **mac**      | Launch another macro<br> `mac "Macro9"` |
| **err**      | Continue if error occurs<br> `wait 2 "Window"`<br>`err` |
| **ret**      | Exit current macro/function<br> `if(i=0) ret` |
| **goto**     | Jump to label<br> `if(i>=10) goto g1`<br>`g1: out "This line is always executed"` |
| **if, else** | Conditional execution<br> `if i<5 ... else ...` |
| **rep, break** | Loop and break<br> `rep 10 ... break` |
| **int, str** | Declare variables<br> `str s="Notepad"`<br>`int x y`<br>`int+ g_var` |

---
# Syntax of QM Macro Code

QM macro text is a sequence of statements. Usually, a statement is a single line of code that performs an operation or declares an identifier.

**Examples:**

```qm
lef+ 10 200 "Notepad"
lef
int a b c
a = b * 100
Func b 1
a = Func(b 1)
```

---

The first and second statements are *macro commands*. They consist of the following *parts*:
- `lef` is the command *keyword*.
- `+` is an *option*.
- `10`, `200`, and `"Notepad"` are *arguments* (the actual values for the command/function parameters).

The third statement declares [variables](../Language/IDH_VARIABLES.html) `a`, `b`, and `c`.

The fourth statement assigns the [expression](../Other/IDP_EXPRESSION.html) `b*100` to variable `a`.

In the fifth statement, the [function](../Language/IDH_FUNCTIONS.html) `Func` is called with arguments `b` and `1`.

In the last statement, function `Func` is called, and its return value is assigned to `a`.

Numbers such as 10, 200, 100, and 1 are *numeric* [constants](../Language/IDP_CONSTANT.html).

`"Notepad"` is a *string constant*.

`=` and `*` are [operators](../Language/IDH_OPERATORS.html).

---

Parts of statements must be separated by spaces (except command/option). In statements with operators (example 4), spaces may be omitted. Arguments can also be separated by commas (`,`).

When using enclosed arguments, the `(` must be immediately after the function name and option character (if any).

---

### Special Characters at the Beginning of a Line

- Space, `;`, `/`, or `\` disables the line (useful for comments).
- To disable/enable lines easily, right-click the selection bar.
- Comments can also follow a statement using `;;`.

**Example:**
```qm
; this is a comment
int a ;; declare integer a
```

---

Tabs or commas are used with flow-control statements (`if`, `rep`, etc).

**Example:**
```qm
; if a is less than 10, left-click, else exit
if a<10
    lef
    a + 1 ;; increment a
else ret
```

---

A single line can contain several statements separated by semicolons (`;`). A semicolon is optional after a statement that begins with a command/function name and has enclosed arguments (or empty parentheses). It's also optional after `else`, `err`, and `case`.

**Examples:**
```qm
lef+ 10 100 Notepad; lef; int a; a = b + 100; Func(a b); b = Func(a b)
rep() if(b>a) b=Func(a b); else break
```

---

## Syntax Descriptions Used in This Help File

Gray symbols in syntax descriptions have the following meanings:

| Syntax Example                 | Meaning                                    |
|-------------------------------|--------------------------------------------|
| `[a]`                         | *a* is optional                            |
| `a\|b`                        | *a* or *b*                                 |
| `a&b`                         | *a* and/or *b*                             |
| `(a b)\|(c d)`                | *a b* or *c d*                             |
| `(space)a`                    | *a* must be preceded by space or semicolon |
| `(tab)a`                      | *a* must be preceded by tab or comma       |
| `...`                         | More parameters or statements              |
| `int a`                       | *a* is a function returning int            |

**Syntax description example:**
```
lef[+|-] [x y] [window] [client]
```
- All parameters in `[]` are optional.
- `[+|-]` means you can use option character `+` or `-` optionally.
- The `lef` keyword at the beginning means `lef` is a command, not a function.

**Real code examples based on the above syntax:**
```qm
lef 10 200 "Notepad"
lef
lef+ 10 200
```
---

# Programming in QM

## Table of Contents

- [Predefined commands and functions](#predefined-commands-and-functions)
- [Constants](#constants)
- [Variables](#variables)
- [Operators](#operators)
- [Functions](#functions)
- [If-else](#if-else)
- [Go to](#go-to)
- [Repeat](#repeat)
- [String manipulation](#string-manipulation)
- [Errors](#errors)
- [Threads](#threads)

---

As described in the [syntax](IDP_SYNTAX.html) topic, QM macro code is a sequence of various statements: macro commands, functions, calculations, [declarations](../Language/IDP_DECLARATION.html), flow-control, and everything needed for programming.  
A single line can contain one statement or several statements separated by semicolons.  
For comments, use a space at the beginning of a line or two semicolons after statements. Tabs at the beginning of a line are used for flow-control statements (`if`, `rep`, etc).

**Example:**

```qm
 if a is less than 10, left-click, else exit
if(a<10)
    lef 5 a "Some Window"; wait 1
    a + 1 ;;increment a
else ret
```

---

## Predefined commands and functions

Quick Macros has about 200 built-in [keywords](IDH_REFERENCE.html), including macro commands, functions, member functions, flow control statements, declaration statements, intrinsic types, compiler directives, and operators.  
You can also use [DLL functions](../Language/IDP_DLL.html), [COM functions](../_COM/IDH_COM.html), and [user-defined functions](../QM_Help/IDH_FUNCTION.html).

QM provides several [features](../QM_Help/IDH_TYPEINFO.html) to simplify programming. You can press **F1** for help on functions and identifiers. Basic syntax or definitions are shown in the QM status bar. To browse and insert available identifiers, use member lists. Some commands can be entered via dialogs or recorded.

---

## Constants

[Constants](../Language/IDP_CONSTANT.html) are simple numeric or string values, such as `45` (integer), `0x1A` (hex integer), `10.57` (float), or `"text"` (string).  
String constants are enclosed in double quotes. To insert a double quote inside a string, use two single quotes (`''`).  
For new line, use `[]`.  
Constants can be assigned to variables, used as arguments, and in expressions with operators.  
You can also define [named constants](../Language/IDP_DEF.html).

---

## Variables

[Variables](../Language/IDH_VARIABLES.html) temporarily store data (numeric, text, etc) at runtime. Data can be changed during various operations.  
Variables can be assigned, used as arguments, and in expressions with operators.

Before using a variable, you must [declare](../Language/IDP_VARIABLES.html) it (except [predefined variables](../Language/IDP_SPECVAR.html)). Declaration includes type and [name](../Other/IDP_IDENTIFIERS.html).  
Common types:  
- `int` (integer values)
- `str` (strings)
- `double` (floating-point)

**Example:**

```qm
int i
str S3
double+ g_var
i=5
S3="text"
g_var=15.477
```

You can use [pointers](../Language/IDH_POINTERS.html) and [arrays](../_COM/IDP_OLE_ARRAY.html):

```qm
ARRAY(str) a.create(10)
a[0]="abc"
```

You can [define new types](../Language/IDP_TYPE.html). User-defined types usually have several member variables.  
For example, type `POINT` has members `x` and `y`:

```qm
POINT p
p.y=10
```

---

## Operators

[Operators](../Language/IDH_OPERATORS.html) are special symbols for assignment, arithmetic, comparison, or other operations.

**Examples:**

```qm
i = 5            ;; assign 5 to i
i + 2            ;; add 2 to i
a = b + 10       ;; a = b + 10
ave = i + j / 2  ;; ave = i + (j / 2)
f = i - (10 * j) + func(a b) * -10 ;; complex expression
str s = "notepad" ;; declare s, assign "notepad"
s + ".exe"       ;; append ".exe"
if(i<10 and s="notepad.exe") i = j/10 ;; logical and comparison
i = Func2(j s (i + 5) f) ;; call function with arguments
lef a-10 100     ;; left click at (a-10, 100)
```

Operators have 3 priority classes:  
1. Arithmetic/bitwise  
2. Comparison (`=`, `!`, `<`, etc)  
3. Logical (`and`, `or`)  

Operators in the same class are evaluated left to right. Use parentheses to change order.

See also:  
- [unary operators](../Language/IDP_OPUNARY.html) (`-` etc)
- [member access operator](../Language/IDP_TYPEUSAGE.html) `.`
- [array element access operator](../_COM/IDP_OLE_ARRAY.html) `[]`

---

## Functions

See also: [functions](../Language/IDH_FUNCTIONS.html), [user-defined functions](../QM_Help/IDH_FUNCTION.html), [sub-functions](../Language/IDP_DIR_SUB.html), [function tips](../QM_Help/IDH_FUNCTIONTIPS.html).

A function is a named code unit that can receive (via arguments) and return values.  
Besides predefined functions, you can create your own.  
Reuse code by placing it in a function and calling it from any macro.

**Examples:**

```qm
Func a "text" 100        ;; call Func with three arguments
a = Func2(10)            ;; call Func2, assign return to a
Func3(a Func4(b c))      ;; nested function calls
d = e + Func5(b c) / 10  ;; use function in expression
```

Some variable types have member functions, called as: variable name, dot, function name.

```qm
str s s2="notepad"
s.from(s2 ".exe")
if(s.end(".exe")) out "s ends with ''.exe''"
```

To create a new [user-defined function](../QM_Help/IDH_FUNCTION.html), select **New Function** from File/New.  
To define return type and parameters, use the [`function`](../Language/IDP_FUNCTION.html) statement at the top.  
To return a value, use the [`ret`](../Flow/IDP_RET.html) statement.

By default, a function can be called from code or launched as a macro.  
To make it callable only from code, start with a line containing space and `/`:

```qm
 /
function'int str'a str&b [int'c]
statements
ret 1
```

- This function returns `int`.  
- It has three parameters: `a`, `b` (by reference), `c` (optional).  
- If not returned explicitly, the return value is 0.

---

## If-else

Use `if` to execute or skip statements depending on a condition.

**Example:**

```qm
if a>0
    out "a is greater than zero"
    a-1
else if a=0
    out "a is equal to zero"
else
    out "a is less than zero"
```

Statements can also be in a single line:

```qm
if(a>0) out "a is greater than zero"; a-1
else if(a=0) out "a is equal to zero"
else out "a is less than zero"
```

For comparing a variable to multiple constant values, use [`sel`](../Flow/IDP_SEL.html).

---

## Go to

The [`goto`](../Flow/IDP_GOTO.html) statement jumps to another place in the code.

**Example:**

```qm
goto g1
statements
 g1
statements
```

Statements after `goto` are skipped; execution resumes after the label (`g1`, with a space before the label).

---

## Repeat

The [`rep`](../Flow/IDP_REP.html) statement repeats the following tab-indented statements.  
You can specify the number of repetitions. To exit early, use `break`.  
Statements can also be in the same line.

**Examples:**

```qm
rep(100) i-1
```

This executes `i-1` 100 times.

```qm
i=0
rep
    if(i>=100) break
    out i
    i+1
```

Equivalent using `for`:

```qm
for i 0 100
    out i
```

---

## String manipulation

QM provides many functions for processing [strings](../str/IDH_STRINGS.html). Use `str` variables to store and manipulate text.

**Example:**

```qm
str s = "Cat" ;; now s is "Cat"
```

### Global string functions

- `val(s)` – numeric value of string s (0 if s doesn't start with digits)
- `find(s "substring")` – index of "substring" in s (or -1 if not found)
- `if(IsCharLower(s[0])) s[0]=CharUpper(+s[0])` – uppercase first character if lowercase

### str member functions

Called with the variable name and dot:

```qm
s.from("word1" ", " "word2")   ;; s = "word1, word2"
s.ucase                        ;; s = "WORD1, WORD2"
str ss.get(s 7 5)              ;; ss = substring of s, starting at 7, length 5
```

You can use `+` and `-` to append and prepend:

```qm
s + ".txt"       ;; append ".txt"
s - "C:\Doc\"    ;; prepend "C:\Doc\"
```

### String comparison

- `=` : equal, case sensitive
- `~` : equal, case insensitive
- `!` : not equal, case sensitive

To compare part of a string, use member functions like `beg`, `mid`, etc.

```qm
if(s~"Monday") ...          ;; s is "Monday" (case insensitive)
if(s.endi(".exe")) ...      ;; s ends with ".exe" (case insensitive)
```

---

## Errors

When you launch a macro, QM [compiles](../QM_Help/IDH_DEBUG.html) it, checking for syntax [errors](../Other/IDP_ERRORS.html).  
On error, QM highlights the error and shows the description. A macro with errors will not run.

At runtime, a macro command may fail, causing a runtime error and macro termination.  
The [`err`](../Flow/IDP_ERR.html) statement allows continuation after a run-time error in the preceding command.

**Examples:**

```qm
clo "Notepad"; err

5 "Notepad"
err
    run "$system$\notepad.exe"
```

In the first example, `err` allows continuation if an error occurs. In the second, on error, the `run "$system$\notepad.exe"` statement is executed.

---

## Threads

[A thread](../Other/IDP_THREADS.html) is like a subprogram in a running program. In QM, it is a running macro or function, including all functions it calls.  
Multiple [function](../QM_Help/IDH_FUNCTION.html) threads can run simultaneously, including several instances of the same function.  
Multiple [macro](../QM_Help/IDH_MACRO.html) threads can run simultaneously if the macro has the 'Run simultaneously' option enabled.

---

# Quick Macros (QM) vs. C++/C# Syntax Comparison

> **Purpose:**  
> This document provides a comprehensive syntax comparison between [Quick Macros (QM)](https://www.quickmacros.com/) and the C++/C# programming languages.  
>  
> **How to use:**  
> If you are familiar with C++ or C# and want to quickly understand QM syntax (or vice versa), use this as a reference.  
>  
> **AI/Reader note:**  
> QM has its own unique syntax, which is more concise and sometimes less formal than C++/C#. Understanding these differences will help you translate logic and patterns between the languages.

---

## Function Declarations

| QM Syntax                                    | C++/C# Syntax               |
|----------------------------------------------|-----------------------------|
| `Function x y`<br>`Function(x y)`<br>`Function(x, y);` | `Function(x, y);`           |

---

## Comments

| QM Syntax               | C++/C# Syntax                                               |
|------------------------|------------------------------------------------------------|
| `code ;;comments`      | `code //comments`<br>`//comments`<br>`/* block of comments */` |

---

## Variable Declarations & Types

### Integer, Floating, String, Array, etc.

#### QM
```
int variable
byte variable
word variable
long variable
double variable
lpstr variable
str variable
BSTR variable
ARRAY(int) variable
int a b(5) c=6
int handle hwnd
int functionAddress=&Function
```

#### C++
```
int variable; // or long variable; also unsigned types: UINT, DWORD
BYTE variable; // or unsigned char variable
WORD variable; // or unsigned short variable
__int64 variable;
double variable;
LPSTR variable; // or char* variable
CString variable; // MFC/ATL
CComBSTR variable; // ATL
CArray <int> variable; // MFC
CSimpleArray <int> variable; // MFC
// More string and array classes are available from various libraries
int a, b=5, c=6;
HANDLE handle; HWND hwnd; // many handle types, in QM all are int
void Function(void); // function has no return value or no parameters
int (__stdcall* FunctionType)(int x, int y); FunctionType functionAddress=Function; // callback type and address
```

#### C#
```
int variable; // uint for unsigned
byte variable; // sbyte for signed
ushort variable; // short for signed, char for Unicode UTF-16 character
long variable; // ulong for unsigned
double variable;
String variable; // Unicode UTF-16 string
int[] variable; // array
int a, b=5, c=6;
void Function(); // no return value
delegate int DelegateType(int x, int y); static DelegateType functionAddress; // callback type and address
```

---

## Variable Scope & Pointers

| QM                          | C++                                                   | C#                                      |
|-----------------------------|-------------------------------------------------------|------------------------------------------|
| `int+ global_variable`      | `int global_variable; // not in function or class`    | `static int global_variable; // in class`|
| `int- thread_variable`      | `__declspec(thread) int thread_variable;`             | `[ThreadStatic] static int thread_variable;` |
| `int local_variable`        | `int local_variable; // in function`                  | `int local_variable; // in function`     |
| `int* pointer1 pointer2`    | `int* pointer1; int* pointer2;`                      |                                          |
| `int& reference_variable=variable` | `int& reference_variable=variable;`            |                                          |
| `int'member_variable int*member_variable2` | `int member_variable; int* member_variable2; // in class` | `int member_variable; // in class`       |

---

## Constants and Enums

| QM                     | C++                                                      | C#                                             |
|------------------------|----------------------------------------------------------|------------------------------------------------|
| `def CO_NSTANT 5`      | `#define CO_NSTANT 5`<br>`const int C1=5;`<br>`enum CONSTANTS { C1=5, C2=5+6 };` | `const int C1=5;`<br>`enum CONSTANTS { C1=5, C2=5+6 };` |
| `def CO_NSTANT2 5+6`   | `#define CO_NSTANT2 (5+6)`                               |                                                |

---

## Output / Printing

| QM          | C++                                         | C#                      |
|-------------|---------------------------------------------|-------------------------|
| `out variable` | `printf("%i", variable); // ANSI`<br>`printf(L"%i", variable); // Unicode` | `Console.WriteLine(variable);` |

---

## Conditionals

### if-else

#### QM
```
if condition
    code
else
    code2
```
#### C++/C#
```c++
if(condition) {
    code
} else {
    code2
}
```

---

## Loops

### for

#### QM
```
for i 0 5
    code
```
#### C++/C#
```c++
for(i=0; i<5; i++) {
    code
}
```

### repeat (counted loop)

#### QM
```
rep 5
    code
```
#### C++/C#
```c++
for(int i=0; i<5; i++) {
    code
}
```

### while

#### QM
```
rep
    if(condition=0) break
    ...
```
#### C++/C#
```c++
while(condition) {
    ...
}
```

### do-while

#### QM
```
rep
    ...
    if(condition=0) break
```
#### C++/C#
```c++
do {
    ...
} while(condition);
```

---

## Switch / Select

#### QM
```
sel i
    case 1
        code
    case 2
        code
    case else
        code
```
#### C++/C#
```c++
switch(i) {
case 1:
    code
    break;
case 2:
    code
    break;
default:
    code
    break;
}
```

---

## Goto and Labels

| QM                 | C++/C#                |
|--------------------|-----------------------|
| `goto label`<br>`... label` | `goto label;`<br>`... label:` |

---

## Error Handling

| QM                | C++                                 | C#                      |
|-------------------|-------------------------------------|-------------------------|
| `code`<br>`err code2` | `try { code } catch(...) { code2 }` | `try { code } catch { code2 }` |

---

## Operators & Expressions

| QM Example                     | C++/C# Equivalent               |
|--------------------------------|---------------------------------|
| `i+1 ;;or: i+=1`               | `i+=1; // or: i++;`             |
| `a = b or c ;;or: a = b || c`  | `a = b || c;`                   |
| `if(a=b) code ;;or: if(a==b) code` | `if(a==b) code // if(a=b) assigns b to a`|
| `x = iif(condition A B)`       | `x = condition ? A : B;`        |

> Most operators are the same in QM, C++, and C#.

---

## Function Definitions and Return

| QM                                              | C++/C#                                      |
|-------------------------------------------------|---------------------------------------------|
| `function'int x [y] ;;function name is not here`<br>`code`<br>`ret 1` | `int FunctionName(int x, int y=0) { code return 1; }` |

---

## DLL / API Imports

| QM                                                         | C++                                                         | C#                                                                                 |
|------------------------------------------------------------|-------------------------------------------------------------|------------------------------------------------------------------------------------|
| `dll "file.dll" int'Function int'x lpstr's`                | `#pragma comment(lib, "file.lib")`<br>`int Function(int x, LPSTR s);` | `[DllImport("file.dll")] public static extern IntPtr Function(int x, [MarshalAs(UnmanagedType.LPStr)] String s);` |

---

## Structs / Types

| QM                    | C++                                        | C#                                         |
|-----------------------|---------------------------------------------|--------------------------------------------|
| `type Type x y double'd` | `struct Type { int x, y; double d; };`   | `struct Type { public int x, y; public double d; };` |

---

## Classes

#### QM
```
class Class --m_private m_public ;;only member variables here
```

#### C++
```c++
class Class {
    int m_private;
public:
    int m_public;
    Class { code } // constructor
    ~Class { code } // destructor
    void MemberFunction(int x, int y); // declaration
};
// function definition elsewhere
void Class::MemberFunction(int x, int y) {
    code
}
```

#### C#
```csharp
class Class {
    int m_private;
    public int m_public;
    public Class { code } // constructor
    ~Class { code } // destructor
    public void MemberFunction(int x, int y) {
        code
    }
};
```

---

## Namespaces / Categories

| QM                                      | C++/C#                      |
|------------------------------------------|-----------------------------|
| `category X : functions`<br>(QM does not have namespaces. Category is similar, but different.) | `namespace X { ... }`       |

---
