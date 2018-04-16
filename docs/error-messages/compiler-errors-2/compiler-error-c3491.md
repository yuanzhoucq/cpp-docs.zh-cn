---
title: "编译器错误 C3491 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8c126ae0533424c19fd29ea48dbea8c3d7e8971
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3491"></a>编译器错误 C3491
“var”：不能在非可变 lambda 中修改按值捕获  
  
 非可变 lambda 表达式不能修改通过值捕获的变量的值。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   用 `mutable` 关键字声明 lambda 表达式，或者  
  
-   将该变量按引用传递到 lambda 表达式的捕获列表。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3491，因为非可变 lambda 表达式的主体修改了捕获变量 `m`：  
  
```  
// C3491a.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) { m = n; }(99); // C3491  
}  
```  
  
## <a name="example"></a>示例  
 下面的示例通过使用 `mutable` 关键字声明 lambda 表达式来解决 C3491：  
  
```  
// C3491b.cpp  
  
int main()  
{  
   int m = 55;  
   [m](int n) mutable { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)