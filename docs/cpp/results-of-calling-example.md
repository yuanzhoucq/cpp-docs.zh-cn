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
ms.openlocfilehash: edbeb187e568b833673d91ef70ff57fbd460659c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179050"
---
# <a name="results-of-calling-example"></a>调用示例的结果

**Microsoft 专用**

## <a name="__cdecl"></a>__cdecl

C 修饰函数名称是 `_MyFunc`。

![CDECL 调用约定](../cpp/media/vc37i01.gif "CDECL 调用约定") <br/>
**__Cdecl**调用约定

## <a name="__stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 修饰名（ **__stdcall**）是 `_MyFunc@20`的。 C++修饰名是特定于实现的。

![&#95;&#95;stdcall 和 thiscall 调用约定](../cpp/media/vc37i02.gif "&#95;&#95;stdcall 和 thiscall 调用约定") <br/>
__stdcall 和 thiscall 调用约定

## <a name="__fastcall"></a>__fastcall

C 修饰名（ **__fastcall**）是 `@MyFunc@20`的。 C++修饰名是特定于实现的。

![Fastcall 的&#95; &#95;调用约定](../cpp/media/vc37i03.gif "Fastcall 的&#95; &#95;调用约定") <br/>
__fastcall 调用约定

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)
