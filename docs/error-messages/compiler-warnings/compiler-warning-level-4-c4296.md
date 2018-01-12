---
title: "编译器警告 （等级 4） C4296 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4296
dev_langs: C++
helpviewer_keywords: C4296
ms.assetid: 9d99aafe-f6bd-4ee0-b8d0-98ce5712274d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af07562daebe4cd6cae0499efafcc9fa3f8b30ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4296"></a>编译器警告（等级 4）C4296
operator： 表达式始终为 false  
  
 值为零的比较操作中使用了无符号的变量。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 下面的示例生成 C4296:  
  
```  
// C4296.cpp  
// compile with: /W4  
#pragma warning(default : 4296)  
int main()  
{  
   unsigned int u = 9;  
   if (u < 0)    // C4296  
      u++;  
   if (u >= 0)   // C4296  
      u++;  
}  
```