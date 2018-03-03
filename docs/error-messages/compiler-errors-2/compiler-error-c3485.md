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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb872161cc82878c7809e6ebcae901db0ba772f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)