---
title: "编译器警告 （等级 2） C4396 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 84f0628de933344eb23dc6325679abdcd3699c3a
ms.openlocfilehash: 8e0538cc5a1ec9279c4d84cb9e23e0d6fabfd77e
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4396"></a>编译器警告（等级 2）C4396
“name”：友元声明引用函数模板的专用化时，无法使用内联说明符  
  
 函数模板专用化不能指定任何[内联](../../cpp/inline-functions-cpp.md)说明符。 编译器发出警告 C4396 并忽略内联说明符。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   从友元函数声明中删除 `inline`、 `__inline`，或 `__forceinline` 说明符。  
  
## <a name="example"></a>示例  
 下面的代码示例演示了一个带有 `inline` 说明符的无效友元函数声明。  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```
