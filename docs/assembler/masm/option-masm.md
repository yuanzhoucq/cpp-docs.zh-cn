---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a8215bf1f816baa490a768fb2cab0b3c2e53e20b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217252"
---
# <a name="option-masm"></a>OPTION (MASM)

启用和禁用在组装器的功能。

## <a name="syntax"></a>语法

> 选项*optionlist*

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

语言的语法是**选项语言：**<em>x</em>，其中*x*是 C、 SYSCALL、 STDCALL、 PASCAL，FORTRAN 或 BASIC 之一。  SYSCALL、 PASCAL，FORTRAN 和 BASIC 不支持与一起使用[。模型](../../assembler/masm/dot-model.md)平面。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>