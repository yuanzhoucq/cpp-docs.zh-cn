---
title: .CODE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59e376fc9c10ab8891b02e4da334341ae0534b73
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="code"></a>.CODE
如果用于[。模型](../../assembler/masm/dot-model.md)，指示代码段的开头。  
  
## <a name="syntax"></a>语法  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`name`|可选参数，用于指定代码段的名称。 默认名称是为小、 较小，压缩和平面 _TEXT[模型](../../assembler/masm/dot-model.md)。 默认名称是*modulename*_TEXT 对于其他模型。|  
  
## <a name="see-also"></a>请参阅  
 [指令引用](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)