---
title: "编译器错误 C3744 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd5c11e88960f2b4332a586d2fe982a8ea94fdbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3744"></a>编译器错误 C3744
__unhook 必须具有针对托管事件至少 3 个自变量  
  
 [__Unhook](../../cpp/unhook.md)函数必须采用三个参数在 c + + 托管扩展编译的程序中使用时。  
  
 `__hook`和`__unhook`与 /clr 编程不兼容。 改为使用 + = 和-= 运算符。  
  
 C3744 才可访问使用过时的编译器选项**/clr:oldSyntax**。  
