---
title: 错误 C1021 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1021
dev_langs:
- C++
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06ec8f9aeca3b88b1c14c8dddfc625aae0b185d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1021"></a>错误 C1021
无效的预处理器命令“string”  
  
 `string` 不是有效的 [预处理器指令](../../preprocessor/preprocessor-directives.md)。 若要解决此错误，请使用对于 `string`有效预处理器名称。  
  
 下面的示例生成 C1021：  
  
```  
// C1021.cpp  
#BadPreProcName    // C1021 delete line  
```