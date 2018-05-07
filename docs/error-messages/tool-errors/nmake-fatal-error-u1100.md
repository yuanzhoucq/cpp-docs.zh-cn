---
title: NMAKE 错误 U1100 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d4ed57c980813c8539fbffed0e41a35048c0571
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE 错误 U1100
宏 macroname 是非法的批处理规则 rule 的上下文中  
  
 当批模式规则的命令块直接或间接地引用非 $< 的特殊文件宏时，NMAKE 生成该错误。  
  
 $< 是批模式规则唯一可以使用的宏。