---
title: "表达式计算器错误 CXX0015 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6f671b39fcc0027fdad5308192c5cbd8b8973717
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0015"></a>表达式计算器错误 CXX0015
表达式太复杂 （堆栈溢出）  
  
 输入的表达式为太复杂或嵌套太深量存储可供 C 表达式计算器。  
  
 由于过多的挂起计算通常会发生溢出。  
  
 重新排列表达式，以便在遇到，可以计算表达式的每个组件，而不是无需等待要计算的表达式的其他部分。  
  
 将表达式拆分为多个命令。  
  
 此错误是与 CAN0015 相同。