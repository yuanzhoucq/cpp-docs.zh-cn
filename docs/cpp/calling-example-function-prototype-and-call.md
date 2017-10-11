---
title: "调用示例： 函数原型和调用 |Microsoft 文档"
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
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 897771dbe2d769744bd5dc119083c9db243d56c0
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="calling-example-function-prototype-and-call"></a>调用示例：函数原型和调用
## <a name="microsoft-specific"></a>Microsoft 专用  
 以下示例显示了使用各种调用约定执行函数调用的结果。  
  
 此示例基于以下函数主干。 将 `calltype` 替换为适当的调用约定。  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 有关详细信息，请参阅[调用结果示例](../cpp/results-of-calling-example.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [调用约定](../cpp/calling-conventions.md)
