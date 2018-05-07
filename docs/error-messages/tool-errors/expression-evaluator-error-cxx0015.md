---
title: 表达式计算器错误 CXX0015 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 945dbda4759fa2989acb0411d1a3216a5e9a036c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0015"></a>表达式计算器错误 CXX0015
表达式太复杂 （堆栈溢出）  
  
 输入的表达式为太复杂或嵌套太深量存储可供 C 表达式计算器。  
  
 由于过多的挂起计算通常会发生溢出。  
  
 重新排列表达式，以便在遇到，可以计算表达式的每个组件，而不是无需等待要计算的表达式的其他部分。  
  
 将表达式拆分为多个命令。  
  
 此错误是与 CAN0015 相同。