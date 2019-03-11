---
title: Microsoft 专用的修饰符
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 119e4d06d0235bbf637eefe8754668d3e90b0c52
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749719"
---
# <a name="microsoft-specific-modifiers"></a>Microsoft 专用的修饰符

本节从以下方面描述特定于 Microsoft 的 C++ 扩展：

- [基于寻址](based-addressing.md)，将一个指针用作其他指针可从中进行偏移的基础的做法

- [函数调用约定](calling-conventions.md)

- 扩展的存储类特性声明[__declspec](declspec.md)关键字

- [__W64](w64.md)关键字

## <a name="microsoft-specific-keywords"></a>Microsoft 专用关键字

许多特定于 Microsoft 的关键字可用于修改声明符以构成派生类型。 有关声明符的详细信息，请参阅[声明符](overview-of-declarators.md)。

|关键字|含义|是否已用于构成派生类型？|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|后跟的名称将 32 位偏移量声明为包含在声明中的 32 位基。|是|
|[__cdecl](cdecl.md)|后跟的名称使用 C 命名和调用约定。|是|
|[__declspec](declspec.md)|后跟的名称指定 Microsoft 特定的存储类特性。|否|
|[__fastcall](fastcall.md)|后跟的名称声明一个函数，该函数使用寄存器（如果可用）而不是用于自变量传递的堆栈。|是|
|[__restrict](extension-restrict.md)|类似于 __declspec ([限制](restrict.md))，但在变量上使用。|No|
|[__stdcall](stdcall.md)|后跟的名称指定遵循标准调用约定的函数。|是|
|[__w64](w64.md)|将数据类型标记为 64 位编译器上较大数据类型。|No|
|[__unaligned](unaligned.md)|指定指向类型或其他数据的指针未对齐。|否|
|[__vectorcall](vectorcall.md)|后跟的名称声明一个函数，如果可能，该函数将使用寄存器（包括 SSE 寄存器）而不是用于参数传递的堆栈。|是|

## <a name="see-also"></a>请参阅

[C++ 语言参考](cpp-language-reference.md)
