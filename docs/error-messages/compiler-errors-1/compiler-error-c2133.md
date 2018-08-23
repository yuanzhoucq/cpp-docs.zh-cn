---
title: 编译器错误 C2133 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2133
dev_langs:
- C++
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 878f6fa4a36e7de28bfc084f7f716d50b52c363a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171908"
---
# <a name="compiler-error-c2133"></a>编译器错误 C2133
identifier： 未知的大小  
  
 未确定大小的数组声明为类、 结构、 联合或枚举的成员。 /Za (ANSI C) 选项不允许未确定大小的成员数组。  
  
 下面的示例生成 C2133:  
  
```  
// C2133.cpp  
// compile with: /Za  
struct X {  
   int a[0];   // C2133 unsized array  
};  
```  
  
 可能的解决方法：  
  
```  
// C2133b.cpp  
// compile with: /c  
struct X {  
   int a[0];   // no /Za  
};  
```