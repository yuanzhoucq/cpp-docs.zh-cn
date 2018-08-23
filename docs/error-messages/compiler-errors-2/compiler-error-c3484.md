---
title: 编译器错误 C3484 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de302987e4ea56e9ee6f29bed1b5842579a8f5b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251951"
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
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)