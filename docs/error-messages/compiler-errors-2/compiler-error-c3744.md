---
title: "编译器错误 C3744 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3744
dev_langs: C++
helpviewer_keywords: C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 87df3fd92ac3fcad9b3e87f02f16b8151e678b77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3744"></a>编译器错误 C3744
__unhook 必须具有针对托管事件至少 3 个自变量  
  
 [__Unhook](../../cpp/unhook.md)函数必须采用三个参数在 c + + 托管扩展编译的程序中使用时。  
  
 `__hook`和`__unhook`与 /clr 编程不兼容。 改为使用 + = 和-= 运算符。  
  
 C3744 才可访问使用过时的编译器选项**/clr:oldSyntax**。  
