---
title: "编译器错误 C3496 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 86c80c4b708bd4315b2ce2ceaf7b61e0629a8b2e
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3496"></a>编译器错误 C3496
“this”始终按值捕获: 已忽略“&”  
  
 不能按引用捕获 `this` 指针。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   按值捕获 `this` 指针。  
  
## <a name="example"></a>示例  
 下面的示例将生成 C3496，因为 lambda 表达式的捕获列表中出现了对 `this` 指针的引用：  
  
```  
// C3496.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      [&this] {}(); // C3496  
   }  
};  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
