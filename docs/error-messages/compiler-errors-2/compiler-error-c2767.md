---
title: "编译器错误 C2767 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2767
dev_langs:
- C++
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe74f9374a6fb74a514fd2655b2e1dbadf02639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2767"></a>编译器错误 C2767
管理或 WinRTarray 维度不匹配： 应有 N 个自变量-提供了 M  
  
 托管数组或 WinRT 数组的声明的格式不正确。 有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 下面的示例生成 C2767，并演示如何修复此错误：  
  
```  
// C2767.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>(2,3); // C2767  
   array<int> ^p2 = new array<int>(2);   // OK  
}  
```