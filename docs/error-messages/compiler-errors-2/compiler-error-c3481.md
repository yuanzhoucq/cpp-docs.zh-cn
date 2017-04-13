---
title: "编译器错误 C3481 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
ms.openlocfilehash: 85157b7c90180eea034a87e3ae165710cefedf19
ms.lasthandoff: 04/12/2017

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
