---
title: "编译器错误 C3495 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
caps.latest.revision: 8
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
ms.openlocfilehash: d5eb9f62cb18d9d94f74caa8925dbba0ed453737
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3495"></a>编译器错误 C3495
“var”：lambda 捕获必须有自动存储持续时间  
  
 不能捕获没有自动存储持续时间的变量，如标记为 `static` 或 `extern`的变量。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   不要将 `static` 或 `extern` 变量传递到 lambda 表达式的捕获列表。  
  
## <a name="example"></a>示例  
 下面的示例将生成 C3495，因为 lambda 表达式的捕获列表中出现了 `static` 变量 `n` ：  
  
```  
// C3495.cpp  
  
int main()  
{  
   static int n = 66;  
   [&n]() { return n; }(); // C3495  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)   
 [(NOTINBUILD)存储类说明符](http://msdn.microsoft.com/en-us/10b3d22d-cb40-450b-994b-08cf9a211b6c)
