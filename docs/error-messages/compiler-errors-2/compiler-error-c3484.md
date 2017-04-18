---
title: "编译器错误 C3484 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a8b8a5f9f51b2c3df57ab8a79e0f514a3c37a2f1
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3484"></a>编译器错误 C3484
返回类型前应为“->”  
  
 你必须在 lambda 表达式的返回类型前提供 `->` 。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   在返回类型前提供 `->` 。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3484：  
  
```  
// C3484a.cpp  
  
int main()  
{  
   return []() . int { return 42; }(); // C3484  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例通过在 lambda 表达式的返回类型之前提供 `->` 来解决 C3484：  
  
```  
// C3484b.cpp  
  
int main()  
{  
   return []() -> int { return 42; }();  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
