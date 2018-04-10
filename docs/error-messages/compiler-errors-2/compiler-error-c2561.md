---
title: 编译器错误 C2561 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 604c5b4ce8c8e1b5477d076a061fdf56fdfd9c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2561"></a>编译器错误 C2561
identifier： 函数必须返回值  
  
 该函数被声明为返回一个值，但函数定义不包含`return`语句。  
  
 此错误可能引起错误的函数原型：  
  
1.  如果该函数不返回一个值，请声明该函数返回类型与[void](../../cpp/void-cpp.md)。  
  
2.  检查所有可能分支的函数返回在原型中声明的类型的值。  
  
3.  C + + 函数，其中包含存储中的返回值的内联程序集例程`AX`注册可能需要的 return 语句。 中的值复制`AX`到临时变量并从函数返回该变量。  
  
 下面的示例生成 C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```