---
title: "编译器错误 C2011 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c599d6add1fa51c6aae7f04019eacdc94f11bb15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2011"></a>编译器错误 C2011
“identifier”：“type”类型重定义  
  
 标识符已定义为 `type`。 检查标识符的重定义。  
  
 如果不止一次将头文件或类型库导入同一个文件，则也有可能生成 C2011。 若要防止多次包含头文件中定义的类型，使用 include 防护或`#pragma`[后](../../preprocessor/once.md)指令标头文件中。  
  
 如果您需要查找重定义的类型的初始声明，则可以使用[/P](../../build/reference/p-preprocess-to-a-file.md)编译器标志生成的预处理的输出传递到编译器。 你可以使用文本搜索工具在输出文件中查找重定义的标识符的实例。  
  
 下面的示例生成了 C2011 并演示了修复此错误的一种方法：  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```