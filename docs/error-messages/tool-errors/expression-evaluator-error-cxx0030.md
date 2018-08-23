---
title: 表达式计算器错误 CXX0030 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669c585c637129c1fb6a480d91b31e5a1264fd22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298111"
---
# <a name="expression-evaluator-error-cxx0030"></a>表达式计算器错误 CXX0030
不可计算的表达式  
  
 顾名思义，调试器的表达式计算器无法获取表达式的值。 一个可能的原因是该表达式引用外部程序的地址空间，则的内存 （取消引用 null 指针是一个示例）。 Windows 不允许在程序的地址空间之外的内存访问。  
  
 你可能想要重写表达式，使用括号来控制的评估顺序。  
  
 此错误是与 CAN0030 相同。