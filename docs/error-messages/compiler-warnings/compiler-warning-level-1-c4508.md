---
title: "编译器警告 （等级 1） C4508 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4508
dev_langs: C++
helpviewer_keywords: C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52139327831be17d6800f30b00f667da7d3b0376
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4508"></a>编译器警告（等级 1）C4508
function： 函数应返回一个值; 如果void 返回类型假定  
  
 函数具有指定没有返回类型。 在这种情况下，也应激发 C4430 和编译器实现的 C4430 （默认值为 int） 报告的修复。  
  
 若要解决此警告，显式声明函数的返回的类型。  
  
 下面的示例生成 C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```