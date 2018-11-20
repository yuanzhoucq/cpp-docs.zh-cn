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
ms.openlocfilehash: dcd1f9002362b7726883c6ce4f74fda9ab593544
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175401"
---
# <a name="results-of-calling-example"></a>调用示例的结果

**Microsoft 专用**

## <a name="cdecl"></a>__cdecl

C 修饰的函数名称是`_MyFunc`。

![CDECL 调用约定](../cpp/media/vc37i01.gif "CDECL 调用约定") <br/>
**__Cdecl**调用约定

## <a name="stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 修饰名 (**__stdcall**) 是`_MyFunc@20`。 C + + 修饰名是特定于实现的。

![&#95;&#95;stdcall 和 thiscall 调用约定](../cpp/media/vc37i02.gif "&#95;&#95;stdcall 和 thiscall 调用约定") <br/>
__stdcall 和 thiscall 调用约定

## <a name="fastcall"></a>__fastcall

C 修饰名 (**__fastcall**) 是`@MyFunc@20`。 C + + 修饰名是特定于实现的。

![调用约定为&#95; &#95;fastcall](../cpp/media/vc37i03.gif "调用约定为&#95; &#95;fastcall") <br/>
__fastcall 调用约定

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)