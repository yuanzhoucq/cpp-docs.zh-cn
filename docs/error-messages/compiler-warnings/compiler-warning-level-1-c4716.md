---
title: "编译器警告 （等级 1） C4716 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4716
dev_langs: C++
helpviewer_keywords: C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a1d9d1e91656e464a5af809f1559eddba5da3291
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4716"></a>编译器警告（等级 1）C4716
“function”必须返回值  
  
 给定的函数未返回一个值。  
  
 只有函数的返回类型为 void 可以使用不随附的返回值返回的命令。  
  
 调用此函数时，将返回未定义的值。  
  
 此警告将自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。  
  
 下面的示例生成 C4716:  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```