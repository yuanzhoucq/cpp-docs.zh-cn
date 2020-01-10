---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318743"
---
# <a name="option"></a>OPTION

启用和禁用组装器的功能。

## <a name="syntax"></a>语法

> **选项** *optionlist*

## <a name="remarks"></a>备注

可用选项包括：

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**仿真**|
|**NOEMULATOR**|**尾声**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**序**|**只读**|**NOREADONLY**|
|**划分**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|

LANGUAGE 的语法是**OPTION LANGUAGE：**<em>x</em>，其中*x*是 C、SYSCALL、STDCALL、PASCAL、FORTRAN 或 BASIC。  不支持 SYSCALL、PASCAL、FORTRAN 和 BASIC [。模型](dot-model.md)平面。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
