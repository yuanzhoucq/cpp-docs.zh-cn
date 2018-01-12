---
title: "编译器警告 （等级 2） C4302 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4302
dev_langs: C++
helpviewer_keywords: C4302
ms.assetid: f5e1c939-e134-4cca-ba1e-9b15a81549ae
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b72b6149e1f904bb78d8c4c1f909faf8b9c0efe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4302"></a>编译器警告（等级 2）C4302
conversion： 从 type 1 的截断 type 2  
  
 编译器检测到从更大的类型转换为更小的类型。 信息可能会丢失。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 下面的示例生成 C4302:  
  
```  
// C4302.cpp  
// compile with: /W2  
#pragma warning(default : 4302)  
int main() {  
   int i;  
   char c = (char) &i;     // C4302  
   short s = (short) &i;   // C4302  
}  
```