---
title: "__cdecl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__cdecl"
  - "__cdecl_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__cdecl 关键字 [C++]"
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# __cdecl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `__cdecl` 是 C 和 C\+\+ 程序的默认调用约定。  由于堆栈已由调用方清理，因此它可以执行 **vararg** 函数。  `__cdecl` 调用约定创建的可执行文件大于 [\_\_stdcall](../cpp/stdcall.md) 调用约定创建的可执行文件，这是因为它要求每个函数调用包括堆栈清理代码。  以下列表显示此调用约定的实现。  
  
|元素|实现|  
|--------|--------|  
|参数传递顺序|从右到左。|  
|堆栈维护职责|调用函数从堆栈中弹出参数。|  
|名称修饰约定|下划线字符 \(\_\) 作为名称的前缀，导出使用 C 链接的 \_\_cdecl 函数时除外。|  
|大小写转换约定|不执行任何大小写转换。|  
  
> [!NOTE]
>  有关相关信息，请参阅[修饰名](../build/reference/decorated-names.md)。  
  
 将 `__cdecl` 修饰符放置在变量或者函数名称的前面。  由于 C 命名和调用约定为默认值，因此你只能在指定 **\/Gv** \(vectorcall\)、**\/Gz** \(stdcall\) 或 **\/Gr** \(fastcall\) 编译器选项时，在 x86 代码中使用 `__cdecl`。  [\/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) 编译器选项强制执行 `__cdecl` 调用约定。  
  
 在 ARM 和 x64 处理器上，接受 `__cdecl`，但编译器一般会忽略它。  按照 ARM 和 x64 上的约定，参数将尽可能传入寄存器，后续参数传递到堆栈中。  在 x64 代码中，使用 `__cdecl` 可重写 **\/Gv** 编译器选项并使用默认 x64 调用约定。  
  
 对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。  也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。  给定此类定义：  
  
```cpp  
struct CMyClass {  
   void __cdecl mymethod();  
};  
```  
  
 此：  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 等效于此：  
  
```cpp  
void __cdecl CMyClass::mymethod() { return; }  
```  
  
## 示例  
 在下面的示例中，将指示编译器对 `system` 函数使用 C 命名和调用约定。  
  
```cpp  
// Example of the __cdecl keyword on function  
int __cdecl system(const char *);  
// Example of the __cdecl keyword on function pointer  
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## 请参阅  
 [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)