---
title: "表达式计算器错误 CXX0030 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0030
dev_langs:
- C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb120103714c3711fb059fa736398458209b52a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0030"></a>表达式计算器错误 CXX0030
不可计算的表达式  
  
 顾名思义，调试器的表达式计算器无法获取表达式的值。 一个可能的原因是该表达式引用外部程序的地址空间，则的内存 （取消引用 null 指针是一个示例）。 Windows 不允许在程序的地址空间之外的内存访问。  
  
 你可能想要重写表达式，使用括号来控制的评估顺序。  
  
 此错误是与 CAN0030 相同。