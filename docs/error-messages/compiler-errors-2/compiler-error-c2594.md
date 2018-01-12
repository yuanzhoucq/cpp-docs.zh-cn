---
title: "编译器错误 C2594 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2594
dev_langs: C++
helpviewer_keywords: C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4cca18672aad77e051ff4428dc115c53cd5ddad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2594"></a>编译器错误 C2594
operator： 从 type1 到 type2 的不明确转换  
  
 从任何转换*type1*到*type2*比任何其他更直接。 我们建议从转换的两个可能的解决方案*type1*到*type2*。 第一个选项是定义从直接转换*type1*到*type2*，和第二个选项是指定的转换从序列*type1*到*type2*。  
  
 下面的示例生成 C2594。 到错误的建议解决方法是一系列的转换：  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```