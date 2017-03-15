---
title: "编译器错误 C3222 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: bd1058f4e33bc70c9021bfb1ceff78af58d09552
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3222"></a>编译器错误 C3222
“parameter”: 无法为托管或 WinRT 类型或泛型函数的成员函数声明默认自变量  
  
不允许声明具有默认自变量的方法参数。 方法的重载形式是一种用于解决此问题的方式。 也就是说，定义具有相同名称但不带参数的方法，然后在方法体中初始化变量。  
  
以下示例生成 C3222：  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  

