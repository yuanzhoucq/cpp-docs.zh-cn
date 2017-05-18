---
title: "编译器错误 C3398 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 66bd229369456da18d8bed60b25b6e6b07e03f27
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3398"></a>编译器错误 C3398
“operator”：无法从“function_signature”转换为“function_pointer”。 源表达式必须是函数符号  
  
 当[__clrcall](../../cpp/clrcall.md)编译时未指定调用约定**/clr**，编译器将生成两个入口点 （地址），每个函数、 一个本机入口点和一个托管的入口点。  
  
 默认情况下，编译器返回本机入口点，但有些情况需要托管入口点（例如将地址分配给 `__clrcall` 函数指针时）。 为了使编译器能够在分配中可靠地选择托管入口点，右侧必须为函数符号。
