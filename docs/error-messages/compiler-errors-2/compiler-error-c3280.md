---
title: 编译器错误 C3280 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3280
dev_langs:
- C++
helpviewer_keywords:
- C3280
ms.assetid: 86dc5bbc-8818-4786-a728-9334268d308b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b47d9f552b84db462734d3ae7dd83fd1257d2044
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249224"
---
# <a name="compiler-error-c3280"></a>编译器错误 C3280
“class”: 无法将托管类型的成员函数编译成非托管函数  
  
 托管的类成员函数不能编译为非托管函数。  
  
 以下示例生成 C3280：  
  
```  
// C3280_2.cpp  
// compile with: /clr  
ref struct A {  
   void func();  
};  
  
#pragma managed(push,off)  
  
void A::func()   // C3280  
{  
}  
  
#pragma managed(pop)  
```  
