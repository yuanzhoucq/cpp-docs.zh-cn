---
title: "编译器错误 C3485 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cd49b93beb54776bf17a9ee2bc5c9816f0964451
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3485"></a>编译器错误 C3485
lambda 定义不能包含任何 cv 限定符  
  
 不能使用 `const` 或 `volatile` 限定符作为 lambda 表达式定义的一部分。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从 lambda 表达式定义中删除 `const` 或 `volatile` 限定符。  
  
## <a name="example"></a>示例  
 以下示例生成 C3485，因为它使用 `const` 限定符作为 lambda 表达式定义的一部分：  
  
```  
// C3485.cpp  
  
int main()  
{  
   auto x = []() const mutable {}; // C3485  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
