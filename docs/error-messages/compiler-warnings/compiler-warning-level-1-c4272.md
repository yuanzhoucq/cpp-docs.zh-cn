---
title: 编译器警告 （等级 1） C4272 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4272
dev_langs:
- C++
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6de736c3226a9d3377769b65604a458c08e25df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4272"></a>编译器警告（等级 1）C4272
function： 标记 __declspec （dllimport）;导入函数时，必须指定本地调用约定。  
  
 它是错误导出函数标记有[__clrcall](../../cpp/clrcall.md)调用约定及编译器发出此警告，如果你尝试导入标记的函数`__clrcall`。  
  
 下面的示例生成 C4272:  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```