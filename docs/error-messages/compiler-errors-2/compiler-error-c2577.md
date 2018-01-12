---
title: "编译器错误 C2577 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2577
dev_langs: C++
helpviewer_keywords: C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2d48df0ef5d4c5a4dff649a54132e75969d92e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2577"></a>编译器错误 C2577
member： 析构函数/终结器不能有返回类型  
  
 析构函数或终结器不能返回值为`void`或任何其他类型。 删除`return`从析构函数定义的语句。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2577。  
  
```  
// C2577.cpp  
// compile with: /c  
class A {  
public:  
   A() {}  
   ~A(){  
      return 0;   // C2577  
   }  
};  
```