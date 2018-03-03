---
title: "表达式计算器错误 CXX0065 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db01baa10191df50c1f319bf8320263657088d75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0065"></a>表达式计算器错误 CXX0065
变量需要堆栈帧  
  
 表达式包含在当前范围内存在但尚未创建的变量。  
  
 当你具有单步执行序言函数但尚未设置函数的堆栈帧或你单步函数的退出代码执行，则可能出现此错误。  
  
 逐句通过 prolog 代码，直到在计算该表达式之前设置的堆栈帧。  
  
 此错误是与 CAN0065 相同。