---
title: "编译器错误 C2748 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2748
dev_langs:
- C++
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f0eaee593630a40a6bffb126e9eab8ed17668e02
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2748"></a>编译器错误 C2748
创建托管数组或 WinRT 数组时必须提供数组大小或数组初始值设定项  
  
 托管数组或 WinRT 数组的格式不正确。 有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 下面的示例生成 C2748，并演示如何修复此错误：  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```
