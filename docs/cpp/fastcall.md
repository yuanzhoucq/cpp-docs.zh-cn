---
title: __fastcall |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fastcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f50239d42c164e2f9c6876e26389eb60e710ed34
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940090"
---
# <a name="fastcall"></a>__fastcall
**Microsoft 专用**  
  
 **__Fastcall**调用约定指定函数的参数是在寄存器中，在可能的情况中传递。 此调用约定仅适用于 x86 体系结构。 以下列表显示此调用约定的实现。  
  
|元素|实现|  
|-------------|--------------------|  
|自变量传递顺序|在参数列表中按从左到右的顺序找到的前两个 DWORD 或更小参数将在 ECX 和 EDX 寄存器中传递；所有其他参数在堆栈上从右向左传递。|  
|堆栈维护职责|已调用函数会弹出显示堆栈中的自变量。|  
|名称修饰约定|At 符号 (\@) 前缀的名称; 名称的列表后缀在号后跟 （采用十进制） 的参数中的字节数。|  
|大小写转换约定|不执行任何大小写转换。|  
  
> [!NOTE]
>  将来版本的编译器可使用其他寄存器来存储参数。  
  
 使用[/Gr](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项将导致每个函数中要作为编译的模块 **__fastcall**除非使用冲突特性声明函数或函数的名称为`main`.  
  
 **__Fastcall**关键字是由接受和忽略编译器面向 ARM 和 x64 体系结构; 在 x64 芯片，按照约定前, 四个参数将传入寄存器在可能的情况下，并传递其他参数在堆栈中。 有关详细信息，请参阅[概述 x64 调用约定](../build/overview-of-x64-calling-conventions.md)。 在 ARM 芯片上，寄存器中可以传递最多四个整数自变量和八个浮点自变量，而其他自变量在堆栈上传递。  
  
 对于非静态类函数，如果函数是超行定义的，则调用约定修饰符不必在超行定义中指定。 也就是说，对于类非静态成员方法，在定义时假定声明期间指定的调用约定。 给定此类定义：  
  
```cpp  
struct CMyClass {  
   void __fastcall mymethod();  
};  
```  
  
 此：  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 等效于此：  
  
```cpp  
void __fastcall CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>示例  
 在下面的示例中，函数 `DeleteAggrWrapper` 是寄存器中传递的参数：  
  
```cpp  
// Example of the __fastcall keyword  
#define FASTCALL    __fastcall  
  
void FASTCALL DeleteAggrWrapper(void* pWrapper);  
// Example of the __ fastcall keyword on function pointer  
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)   
 [关键字](../cpp/keywords-cpp.md)
