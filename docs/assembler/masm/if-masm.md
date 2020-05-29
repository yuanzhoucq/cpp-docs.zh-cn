---
title: IF (MASM)
ms.date: 12/17/2019
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 6e63f5c8075b3c94370ad8863d224c097cf0ecdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440745"
---
# <a name="if"></a>IF

*如果表达式1为 true* （非零） *，则授予* *ifstatements*的程序集; 如果*表达式*1 为 false （0 *），则*为 true。

## <a name="syntax"></a>语法

> **如果***表达式*=\
> *if-语句*\
> ⟦**ELSEIF** *表达式*2\
> *elseif-语句*⟧ \
> ⟦**ELSE**\
> *else-语句*⟧ \
> **ENDIF**

## <a name="remarks"></a>备注

以下指令可以替换为[ELSEIF](elseif-masm.md)： **ELSEIFB**、 **ELSEIFDEF**、 **ELSEIFDIF**、 **ELSEIFDIFI**、 **ELSEIFE**、 **ELSEIFIDN**、 **ELSEIFIDNI**、 **ELSEIFNB**和**ELSEIFNDEF**。 （可选）如果上一个表达式为 false，则汇编*else 语句*。 请注意，将在程序集时间对表达式进行计算。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
