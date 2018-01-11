---
title: "编译器警告 （等级 3） C4280 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4280
dev_langs: C++
helpviewer_keywords: C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 928663fcddad52ade061f4aa2fefa73e63b9cd4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4280"></a>编译器警告（等级 3）C4280
operator-> 是自递归通过类型 type  
  
 你的代码错误地允许**operator->**调用自身。  
  
 下面的示例生成 C4280:  
  
```  
// C4280.cpp  
// compile with: /W3 /WX  
struct A  
{  
   int z;  
   A& operator ->();  
};  
  
void f(A y)  
{  
   int i = y->z; // C4280  
}  
```