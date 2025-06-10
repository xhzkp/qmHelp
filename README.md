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

> _End of comparison.  
> For further details on Quick Macros syntax, see the [official documentation]([https://www.quickmacros.com/help/](https://xhzkp.github.io/qmHelp/QM_Help/IDH_QUICK.html) 
