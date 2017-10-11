---
title: "编译器错误 C2589 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5301caf0b52e61000a804e1d73b76343a8b7b2eb
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2589"></a>编译器错误 C2589
identifier： 非法的标记，在右侧::  
  
 如果类、 结构或联合名称显示范围解析运算符 （双冒号） 的左侧，在右侧的令牌必须是类、 结构或联合成员。 否则，任何全局标识符可以出现在右侧。  
  
 范围解析运算符无法进行重载。  
  
 下面的示例生成 C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```
