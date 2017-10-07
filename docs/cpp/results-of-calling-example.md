---
title: "调用示例的结果 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 5a1d6bf1c1d3cf2a57a74b7994766e940488a8e8
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="results-of-calling-example"></a>调用示例的结果
## <a name="microsoft-specific"></a>Microsoft 专用  
  
## <a name="cdecl"></a>__cdecl  
 C 修饰函数名为“_MyFunc”。  
  
 ![CDECL 调用约定](../cpp/media/vc37i01.gif "vc37I01")  
__cdecl 调用约定  
  
## <a name="stdcall-and-thiscall"></a>__stdcall 和 thiscall  
 C 修饰名 (`__stdcall`) 是"_MyFunc@20。" 该 C ++ 修饰名是专用的。  
  
 ![&#95; &#95; stdcall 和 thiscall 调用约定](../cpp/media/vc37i02.gif "vc37I02")  
__stdcall 和 thiscall 调用约定  
  
## <a name="fastcall"></a>__fastcall  
 C 修饰名 (`__fastcall`) 是"@MyFunc@20。" 该 C ++ 修饰名是专用的。  
  
 ![调用约定 &#95; &#95; fastcall](../cpp/media/vc37i03.gif "vc37I03")  
__fastcall 调用约定  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [调用示例：函数原型和调用](../cpp/calling-example-function-prototype-and-call.md)
