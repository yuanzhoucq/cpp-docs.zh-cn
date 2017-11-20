---
title: "编译器警告 （等级 3） C4646 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4646
dev_langs: C++
helpviewer_keywords: C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 50ecb1bbdd1dbb9445af6bb9987a2f2a4250b215
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4646"></a>编译器警告（等级 3）C4646
用 __declspec(noreturn) 声明的函数有非 void 返回类型  
  
 标记有 [noreturn](../../cpp/noreturn.md) `__declspec` 修饰符的函数应有 [void](../../cpp/void-cpp.md) 返回类型。  
  
 下面的示例生成 C4646：  
  
```  
// C4646.cpp  
// compile with: /W3 /WX  
int __declspec(noreturn) TestFunction()  
{   // C4646  make return type void  
}  
```