---
title: "选项 (MASM) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: option
dev_langs: C++
helpviewer_keywords: OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f449606b143bfbf188e878b261f3d35017846862
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**偏移量**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**序言**|**READONLY**|**NOREADONLY**|  
|**作用域**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|  
  
 语言的语法是**选项语言：***x*，其中*x*是 C、 SYSCALL、 STDCALL、 PASCAL、 FORTRAN 或 BASIC 之一。  SYSCALL、 PASCAL、 FORTRAN 和 BASIC 不支持用于[。模型](../../assembler/masm/dot-model.md)平面。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)