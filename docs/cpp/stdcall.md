---
title: "__stdcall | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__stdcall_cpp"
  - "__stdcall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__stdcall 关键字 [C++]"
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __stdcall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `__stdcall` 调用约定用于调用 Win32 API 函数。  被调用方将清理堆栈，以便让编译器生成 **vararg** 函数 `__cdecl`。  使用此调用约定的函数需要一个函数原型。  
  
## 语法  
  
```  
  
return-type __stdcall function-name[(argument-list)]  
```  
  
## 备注  
 以下列表显示此调用约定的实现。  
  
|元素|实现|  
|--------|--------|  
|参数传递顺序|从右到左。|  
|参数传递约定|按值，除非传递指针或引用类型。|  
|堆栈维护职责|调用的函数从堆栈中弹出自己的参数。|  
|名称修饰约定|下划线 \(\_\) 是名称的前缀。  名称后跟后面是参数列表中的字节数（采用十进制）的符号 \(@\)。  因此，声明为 `int func( int a, double b )` 的函数按如下所示进行修饰：`_func@12`|  
|大小写转换约定|无|  
  
 [\/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) 编译器选项为未使用不同调用约定显式声明的所有函数指定 `__stdcall`。  
  
 使用 `__stdcall` 修饰符声明的函数与使用 [\_\_cdecl](../cpp/cdecl.md) 声明的函数以相同的方式返回值。  
  
 在 ARM 和 x64 处理器上，`__stdcall` 由编译器接受和忽略；在 ARM 和 x64 体系结构上，按照约定，参数将传入寄存器（如果可能）且后续参数将在堆栈上传递。  
  
 对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。  也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。  给定此类定义，  
  
```cpp  
struct CMyClass {  
   void __stdcall mymethod();  
};  
```  
  
 this  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 等效于此  
  
```cpp  
void __stdcall CMyClass::mymethod() { return; }  
```  
  
## 示例  
 在以下示例中，使用 \_\_**stdcall** 将生成所有作为标准调用处理的 `WINAPI` 函数类型：  
  
```c  
// Example of the __stdcall keyword  
#define WINAPI __stdcall  
// Example of the __stdcall keyword on function pointer  
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## 请参阅  
 [参数传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)