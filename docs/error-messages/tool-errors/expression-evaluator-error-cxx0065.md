---
title: 表达式计算器错误 CXX0065 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78c25c9c6bde27219f10e4047dc7a6ab416f55d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297532"
---
# <a name="expression-evaluator-error-cxx0065"></a>表达式计算器错误 CXX0065
变量需要堆栈帧  
  
 表达式包含在当前范围内存在但尚未创建的变量。  
  
 当你具有单步执行序言函数但尚未设置函数的堆栈帧或你单步函数的退出代码执行，则可能出现此错误。  
  
 逐句通过 prolog 代码，直到在计算该表达式之前设置的堆栈帧。  
  
 此错误是与 CAN0065 相同。