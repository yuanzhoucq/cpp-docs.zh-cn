---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: d4b650542a3a85c8f0008374abef02686c5491a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188917"
---
# <a name="__fastcall"></a>__fastcall

**Microsoft 专用**

**__Fastcall**调用约定指定函数的参数在寄存器中传递（如果可能）。 此调用约定仅适用于 x86 体系结构。 以下列表显示此调用约定的实现。

|元素|实现|
|-------------|--------------------|
|参数传递顺序|在自变量列表中按从左到右的顺序找到的前两个 DWORD 或更小自变量将在 ECX 和 EDX 寄存器中传递；所有其他自变量在堆栈上从右向左传递。|
|堆栈维护职责|已调用函数会弹出显示堆栈中的参数。|
|名称修饰约定|At 符号（\@）是名称的前缀;in 符号后跟参数列表中的字节数（以十进制为单位）是名称的后缀。|
|大小写转换约定|不执行任何大小写转换。|

> [!NOTE]
> 将来版本的编译器可使用其他寄存器来存储参数。

使用[/Gr](../build/reference/gd-gr-gv-gz-calling-convention.md)编译器选项将导致模块中的每个函数编译为 **__fastcall** ，除非该函数是使用冲突特性声明的，或者该函数的名称 `main`。

面向 ARM 和 x64 体系结构的编译器接受并忽略 **__fastcall**关键字;在 x64 芯片上，按照约定，前四个参数在寄存器中传递（如果可能），而其他参数在堆栈上传递。 有关详细信息，请参阅[X64 调用约定](../build/x64-calling-convention.md)。 在 ARM 芯片上，寄存器中可以传递最多四个整数参数和八个浮点参数，而其他参数在堆栈上传递。

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

为了与早期版本兼容， **_fastcall**是 **__fastcall**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

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

## <a name="see-also"></a>另请参阅

[自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)<br/>
[关键字](../cpp/keywords-cpp.md)
