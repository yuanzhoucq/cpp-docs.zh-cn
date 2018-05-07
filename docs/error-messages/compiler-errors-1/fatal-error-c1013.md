---
title: 错误 C1013 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00b5dae643ec20e9d7d8a8dcdf41d9debe7e6b7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1013"></a>错误 C1013
编译器限制 : 左括号太多  
  
 表达式在单个表达式中包含太多级别的括号。 简化表达式，或将其分解为多个语句。  
  
 在 Visual C++ 6.0 Service Pack 3 之前，单个表达式中嵌套括号的上限是 59 个。 目前，嵌套括号的上限是 256 个。