---
title: 别名 (MASM) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b14e1c41a448d0cb7014dabc50a42305249938f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="alias-masm"></a>ALIAS (MASM)
**别名**指令创建的函数的备用名称。  这样可以创建多个名称对于函数，或创建允许链接器 (LINK.exe) 以将旧的函数映射到新函数的库。  
  
## <a name="syntax"></a>语法  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### <a name="parameters"></a>参数  
 `actual-name`  
 函数或过程的实际名称。  角度括号是必需的。  
  
 `alias`  
 备用或别名的名称。  角度括号是必需的。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)