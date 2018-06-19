---
title: 编译器错误 C2448 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2448
dev_langs:
- C++
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc62d7aeba0a128c9b736586e6c1502227de717
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226044"
---
# <a name="compiler-error-c2448"></a>编译器错误 C2448
identifier： 函数样式初始值设定项似乎是一个函数定义  
  
 函数定义不正确。  
  
 可以由旧式 C 语言形参列表导致此错误。  
  
 下面的示例生成 C2448:  
  
```  
// C2448.cpp  
void func(c)  
   int c;  
{}   // C2448  
```