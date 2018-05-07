---
title: 资源编译器错误 RC2151 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8349aa14de6aec96fa1b526cbcffbe79036f804d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2151"></a>资源编译器错误 RC2151
不能重复使用字符串常量  
  
 使用相同的值在两次**STRINGTABLE**语句。 请确保您没有混合重叠十进制和十六进制值。  
  
 在每个 ID **STRINGTABLE**必须是唯一的。 为最大效率，请使用在 16 的倍数启动连续常数。