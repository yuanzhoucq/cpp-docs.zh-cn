---
title: 编译器警告 （等级 4） C4235 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc63640bc58caefa281b9207b9796ffdf387a7a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4235"></a>编译器警告（等级 4）C4235
使用的非标准扩展: keyword 关键字不支持这种体系结构  
  
 编译器不支持您使用的关键字。  
  
 此警告将自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使 C4235 等级 2 警告，可使用以下代码行  
  
```  
#pragma warning(2:4235)  
```  
  
 在你的源代码文件。