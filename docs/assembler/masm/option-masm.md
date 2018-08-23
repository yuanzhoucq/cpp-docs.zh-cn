---
title: 选项 (MASM) |Microsoft 文档
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
ms.openlocfilehash: 80291c805cad3ef041fffc58983ff399da07c9d9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057716"
---
# <a name="option-masm"></a>OPTION (MASM)
启用和禁用汇编程序的功能。  
  
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
|**PROC**|**序言**|**READONLY**|**NOREADONLY**|  
|**作用域**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 语言的语法是 **选项语言: * * * x*，其中*x*是 C、 SYSCALL、 STDCALL、 PASCAL、 FORTRAN 或 BASIC 之一。  SYSCALL、 PASCAL、 FORTRAN 和 BASIC 不支持用于[。模型](../../assembler/masm/dot-model.md)平面。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)