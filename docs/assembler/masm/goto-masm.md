---
title: GOTO (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9eecdab2fe91de0aae656b37c6fddafe658e60c0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="goto-masm"></a>GOTO (MASM)
将程序集传输到标记的行 **: * * * macrolabel*。  
  
## <a name="syntax"></a>语法  
  
```  
  
GOTO   
macrolabel  
  
```  
  
## <a name="remarks"></a>备注  
 **GOTO**允许仅在内[宏](../../assembler/masm/macro.md)，[为](../../assembler/masm/for-masm.md)， [FORC](../../assembler/masm/forc.md)，[重复](../../assembler/masm/repeat.md)，和**时**块。 标签必须是在行上唯一的指令，并且必须由前导冒号前面。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)