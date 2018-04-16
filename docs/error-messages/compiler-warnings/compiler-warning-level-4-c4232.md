---
title: "编译器警告 （等级 4） C4232 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0b8725ca2a7ee6c5f512559eecdb6b01ac4c6a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4232"></a>编译器警告（等级 4）C4232
使用的非标准扩展: identifier: dllimport dllimport 地址不是静态的的标识不能保证  
  
 在 Microsoft 扩展 (/Ze) 中，您可以赋予非静态值，像使用声明的函数地址**dllimport**修饰符。 在 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，这将导致错误。  
  
 下面的示例生成 C4232:  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```