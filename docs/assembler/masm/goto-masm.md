---
title: GOTO (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c86a9b5bc83110f20dccf73f51b1e1aabc693db2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
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