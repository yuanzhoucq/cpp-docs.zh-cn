---
title: 选项 (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2dcbc55d6a2d033cde3b6189618afd67bdc3fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221504"
---
# <a name="option-masm"></a>OPTION (MASM)
启用和禁用在组装器的功能。  
  
## <a name="syntax"></a>语法  
  
```  
  
OPTION   
optionlist  
  
```  
  
## <a name="remarks"></a>备注  
 可用选项包括：  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**仿真程序**|  
|**NOEMULATOR**|**尾声**|**EXPR16**|**EXPR32**|  
|**语言**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**序言**|**只读**|**NOREADONLY**|  
|**作用域**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 语言的语法是**选项语言：**<em>x</em>，其中*x*是 C、 SYSCALL、 STDCALL、 PASCAL，FORTRAN 或 BASIC 之一。  SYSCALL、 PASCAL，FORTRAN 和 BASIC 不支持与一起使用[。模型](../../assembler/masm/dot-model.md)平面。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)