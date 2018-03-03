---
title: "编译器错误 C2600 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 407598a68df37aa130ce26e4f02e98de975ab527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2600"></a>编译器错误 C2600
function： 不能定义 （必须在声明类第一次） 的编译器生成的特殊成员函数  
  
 在为类定义成员函数（如构造函数或析构函数）之前，必须在类中声明它们。 如果没有在类中声明，则编译器会生成默认的构造函数和析构函数（称为特殊成员函数）。 但是，如果在类中定义这些函数中没有匹配声明的函数，则编译器将检测到冲突。  
  
 若要修复此错误，请在类声明中，声明你在类声明以外定义的每个成员函数。  
  
 以下示例生成 C2600：  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```