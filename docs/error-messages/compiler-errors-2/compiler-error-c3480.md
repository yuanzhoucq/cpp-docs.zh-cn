---
title: "编译器错误 C3480 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3480
dev_langs:
- C++
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d84314d20ea00e880981e418c2b5b11008f74229
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3480"></a>编译器错误 C3480
“var”：lambda 捕获变量必须来自封闭函数范围  
  
 Lambda 捕获变量不是来自封闭函数范围。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从 lambda 表达式的捕获列表中删除该变量。  
  
## <a name="example"></a>示例  
 下面的示例将生成 C3480，因为变量 `global` 不是来自封闭函数范围：  
  
```  
// C3480a.cpp  
  
int global = 0;  
int main()  
{  
   [&global] { global = 5; }(); // C3480  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例通过从 lambda 表达式的捕获列表中删除变量 `global` 来解决 C3480：  
  
```  
// C3480b.cpp  
  
int global = 0;  
int main()  
{  
   [] { global = 5; }();  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
