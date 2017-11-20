---
title: "编译器错误 C2032 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2032
dev_langs: C++
helpviewer_keywords: C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 81bbe4c9e5242f68a5e0e304858c13c9274c1743
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2032"></a>编译器错误 C2032
identifier： 函数不能为结构/联合 structorunion 的成员  
  
 结构或联合具有成员函数时，这允许 c + + 中但不是在 c。若要解决此错误，请编译为 c + + 程序，或删除成员函数。  
  
 下面的示例生成 C2032:  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 可能的解决方法：  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```