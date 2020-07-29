---
title: 调用示例的结果
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 1bf5fe62b8ef2b7a37bf72b7a40e5d47af3f3961
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225873"
---
# <a name="results-of-calling-example"></a>调用示例的结果

**Microsoft 专用**

## <a name="__cdecl"></a>__cdecl

C 修饰函数名称为 `_MyFunc` 。

![CDECL 调用约定](../cpp/media/vc37i01.gif "CDECL 调用约定") <br/>
**`__cdecl`** 调用约定

## <a name="__stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 修饰名（ **`__stdcall`** ）为 `_MyFunc@20` 。 C + + 修饰名称是特定于实现的。

![&#95;&#95;stdcall 和 thiscall 调用约定](../cpp/media/vc37i02.gif "&#95;&#95;stdcall 和 thiscall 调用约定") <br/>
__stdcall 和 thiscall 调用约定

## <a name="__fastcall"></a>__fastcall

C 修饰名（ **`__fastcall`** ）为 `@MyFunc@20` 。 C + + 修饰名称是特定于实现的。

![ &#95;&#95;fastcall 的调用约定](../cpp/media/vc37i03.gif " &#95;&#95;fastcall 的调用约定") <br/>
__fastcall 调用约定

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)
