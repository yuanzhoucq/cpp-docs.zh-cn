---
title: 调用示例的结果 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5687adfada8657ae26edd9001db8990ff08864e9
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894689"
---
# <a name="results-of-calling-example"></a>调用示例的结果

**Microsoft 专用**

## <a name="cdecl"></a>__cdecl
C 修饰的函数名称是`_MyFunc`。

![CDECL 调用约定](../cpp/media/vc37i01.gif "vc37I01")  
**__Cdecl**调用约定

## <a name="stdcall-and-thiscall"></a>__stdcall 和 thiscall

C 修饰名 (**__stdcall**) 是`_MyFunc@20`。 C + + 修饰名是特定于实现的。

![&#95;&#95;stdcall 和 thiscall 调用约定](../cpp/media/vc37i02.gif "vc37I02")  
__stdcall 和 thiscall 调用约定

## <a name="fastcall"></a>__fastcall

C 修饰名 (**__fastcall**) 是`@MyFunc@20`。 C + + 修饰名是特定于实现的。

![调用约定为&#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
__fastcall 调用约定

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)