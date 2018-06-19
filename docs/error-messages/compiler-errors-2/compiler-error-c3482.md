---
title: 编译器错误 C3482 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad7ea983d13f03add2772da173062b1ad5652d3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258629"
---
# <a name="compiler-error-c3482"></a>编译器错误 C3482
“this”只能在非静态成员函数中用作 lambda 捕获  
  
 不能将 `this` 传递至在静态方法或全局函数中声明的 lambda 表达式的捕获列表中。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   将封闭函数转换为非静态方法，或  
  
-   从 lambda 表达式的捕获列表中删除 `this` 指针。  
  
## <a name="example"></a>示例  
 以下示例生成 C3482：  
  
```  
// C3482.cpp  
// compile with: /c  
  
class C  
{  
public:  
   static void staticMethod()  
   {  
      [this] {}(); // C3482  
   }  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)