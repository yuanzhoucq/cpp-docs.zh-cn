---
title: "编译器错误 C3626 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3626
dev_langs:
- C++
helpviewer_keywords:
- C3626
ms.assetid: 43926e2b-1ba9-4a43-9343-c58449cbb336
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9acd9c4e08c082d27fbc564031c515ca2a680d30
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3626"></a>编译器错误 C3626
keyword: __event 关键字只能在 COM 接口、 成员函数和都是指向委托的数据成员  
  
 未正确使用一个关键字。  
  
 下面的示例生成 C3626:  
  
```  
// C3626.cpp  
// compile with: /c  
struct A {  
   __event int i;   // C3626  
// try the following line instead  
// __event int i();  
};  
```
