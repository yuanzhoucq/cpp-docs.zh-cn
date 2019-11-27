---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: ed7b9e63bb19dcc16539dbdaaf1f6a7f16566b3c
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397455"
---
# <a name="if-masm"></a>IF (MASM)

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

以下指令可以替换为[ELSEIF](../../assembler/masm/elseif-masm.md)： **ELSEIFB**、 **ELSEIFDEF**、 **ELSEIFDIF**、 **ELSEIFDIFI**、 **ELSEIFE**、 **ELSEIFIDN**、 **ELSEIFIDNI**、 **ELSEIFNB**和**ELSEIFNDEF**。 （可选）如果上一个表达式为 false，则汇编*else 语句*。 请注意，将在程序集时间对表达式进行计算。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
