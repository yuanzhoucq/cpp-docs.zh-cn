---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 0f90ab0115c3dde894d468bbbe60ffa0193b8336
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395170"
---
# <a name="option-masm"></a>OPTION (MASM)

启用和禁用组装器的功能。

## <a name="syntax"></a>语法

> **选项** *optionlist*

## <a name="remarks"></a>备注

可用选项包括：

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**仿真**|
|**NOEMULATOR**|**尾声**|**EXPR16**|**EXPR32**|
|**语言**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**抵销**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**序**|**只读**|**NOREADONLY**|
|**划分**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|

LANGUAGE 的语法是**OPTION LANGUAGE：** <em>x</em>，其中*x*是 C、SYSCALL、STDCALL、PASCAL、FORTRAN 或 BASIC。  与一起使用时，SYSCALL、PASCAL、FORTRAN 和 BASIC 不受支持[。模型](../../assembler/masm/dot-model.md)平面。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
