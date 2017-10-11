---
title: "编译器错误 C2849 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2849
dev_langs:
- C++
helpviewer_keywords:
- C2849
ms.assetid: e28f6b3e-e0e7-4f92-b006-ebaa81d368e6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 649c4ed4231518c7604f0a7f32ceb5a9632a4f71
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2849"></a>编译器错误 C2849
析构函数： 接口不能具有析构函数  
  
 Visual c + +[接口](../../cpp/interface.md)不能具有析构函数。  
  
 下面的示例生成 C2849:  
  
```  
// C2849.cpp  
// compile with: /c  
__interface C {  
   ~C();   // C2849 destructor not allowed in an interface  
};  
```
