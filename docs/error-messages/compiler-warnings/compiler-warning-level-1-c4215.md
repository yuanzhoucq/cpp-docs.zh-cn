---
title: 编译器警告 （等级 1） C4215 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4215
dev_langs:
- C++
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d5e07b9382c24f82f3e7d84fe82aee9dd91ca19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277600"
---
# <a name="compiler-warning-level-1-c4215"></a>编译器警告（等级 1）C4215
使用的非标准扩展： 长浮点  
  
 默认 Microsoft 扩展 (/Ze) 将**长浮点**作为**double**。 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 却没有。 使用**double**为了保持兼容性。  
  
 下面的示例生成 C4215:  
  
```  
// C4215.cpp  
// compile with: /W1 /LD  
long float a;   // C4215  
  
// use the line below to resolve the warning  
// double a;  
```