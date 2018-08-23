---
title: 编译器错误 C2589 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c15589358979f554a9c17114f7d78b05dd83c472
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230748"
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