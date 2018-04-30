---
title: 标签 (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Label
dev_langs:
- C++
helpviewer_keywords:
- LABEL directive
ms.assetid: 39ec44e8-91e6-4f3c-8cf0-b66479974e42
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4189d1ae5cf79d0ecf8cc07fa940e754fe314a6d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="label-masm"></a>LABEL (MASM)
通过分配的当前的位置计数器值创建一个新标签与给定`type`到*名称*。  
  
## <a name="syntax"></a>语法  
  
```  
  
      name LABEL type  
name LABEL [[NEAR | FAR | PROC]] PTR [[type]]   
```  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)