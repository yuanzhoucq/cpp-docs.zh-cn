---
title: "编译器错误 C3481 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 33bd3d85a4cf44741d59ccb81259babd34704b69
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3481"></a>编译器错误 C3481
“var”：未找到 lambda 捕获变量  
  
 编译器未找到传递给 lambda 表达式捕获列表的变量的定义。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从 lambda 表达式的捕获列表中删除该变量。  
  
## <a name="example"></a>示例  
 下面的示例由于未定义变量 `n` 而生成 C3481：  
  
```  
// C3481.cpp  
  
int main()  
{  
   [n] {}(); // C3481  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
