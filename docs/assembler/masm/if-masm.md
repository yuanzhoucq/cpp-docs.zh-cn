---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 2b91698640e028bf91d822c12b85ded651a04d8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203059"
---
# <a name="if-masm"></a>IF (MASM)

授予的程序集*ifstatements*如果*expression1*为 true （非零） 或*elseifstatements*如果*expression1*为 false (0) 和*expression2*为 true。

## <a name="syntax"></a>语法

> IF *expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[其他<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>备注

以下指令可能会替换为[ELSEIF](../../assembler/masm/elseif-masm.md):**ELSEIFB**， **ELSEIFDEF**， **ELSEIFDIF**， **ELSEIFDIFI**， **ELSEIFE**， **ELSEIFIDN**， **ELSEIFIDNI**， **ELSEIFNB**，并**ELSEIFNDEF**。 （可选） 组装*elsestatements*如果上一个表达式为 false。 请注意，在程序集时计算这些表达式。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>