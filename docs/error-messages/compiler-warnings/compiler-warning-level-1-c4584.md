---
title: "编译器警告 （等级 1） C4584 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4584
dev_langs: C++
helpviewer_keywords: C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c17d8871d16cd2eec6b46e01d9c1779f3440398
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4584"></a>编译器警告（等级 1）C4584
class1： 已基类的 class3 移基类 class2。  
  
 你定义的类继承自两个类，其中一个继承自其他。 例如:   
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 在这种情况下，将会发出警告类 C 从类 A 和 B，后者也继承自类 a。 类继承因此此警告充当提醒必须完全限定的成员从这些基类的类的用法，或由于语意不明确，哪个类成员中，你将引用不会生成编译器错误。