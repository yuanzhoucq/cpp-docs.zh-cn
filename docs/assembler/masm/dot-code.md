---
title: ".代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .CODE
dev_langs: C++
helpviewer_keywords: .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 150b5a0c26be3c3c4d0412157179ebfcbec128e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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