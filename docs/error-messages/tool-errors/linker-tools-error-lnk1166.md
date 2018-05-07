---
title: 链接器工具错误 LNK1166 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1166
dev_langs:
- C++
helpviewer_keywords:
- LNK1166
ms.assetid: d69548a8-0efb-44e1-90b7-b27636a4b575
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 474d4ad146edf4411bd9734a6ec4482273c065dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1166"></a>链接器工具错误 LNK1166
无法调整代码偏移量 = 偏移量，va = 值  
  
 链接无法填充所需的代码。  
  
 某些指令不允许在某些处理器上跨页边界。 链接尝试将添加填充代码来纠正这种情况。 在这种情况下，链接可能不解决此问题。