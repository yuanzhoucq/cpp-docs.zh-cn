---
title: .DOSSEG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3817cfe98758faf86ea87d74e02657598c3e806b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054879"
---
# <a name="dosseg"></a>.DOSSEG
根据 MS-DOS 段约定的段进行排序： 代码第一次，然后段不在 DGROUP，和在 DGROUP 然后段。  
  
## <a name="syntax"></a>语法  
  
```  
  
.DOSSEG  
  
```  
  
## <a name="remarks"></a>备注  
 段中 DGROUP 遵循此顺序： 段不在面临或堆栈，然后面临段，并最后的堆栈段。 主要用于确保 MASM 独立程序中的 CodeView 支持。 与相同[DOSSEG](../../assembler/masm/dosseg.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)