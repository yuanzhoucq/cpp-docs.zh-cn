---
title: "编译器错误 C2860 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2860
dev_langs: C++
helpviewer_keywords: C2860
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1890a407fece8d2ecdd81c90c12a8d28dd57186
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2860"></a>编译器错误 C2860
void 不能是自变量类型，除外 (void)  
  
 类型`void`不能用作参数类型与其他参数。  
  
 下面的示例生成 C2860:  
  
```  
// C2860.cpp  
// compile with: /c  
void profunc1(void, int i);   // C2860  
void func10(void);   // OK  
```