---
title: 如果 (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0cce834924f7fc147b1ef301d5bd345dfd2973
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685302"
---
# <a name="if-masm"></a>IF (MASM)

授予的程序集*ifstatements*如果*expression1*为 true （非零） 或*elseifstatements*如果*expression1*为 false (0) 和*expression2*为 true。

## <a name="syntax"></a>语法

> 如果*expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[其他<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>备注

以下指令可能会替换为[ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**， **ELSEIFDEF**， **ELSEIFDIF**， **ELSEIFDIFI**， **ELSEIFE**， **ELSEIFIDN**， **ELSEIFIDNI**， **ELSEIFNB**，和**ELSEIFNDEF**. （可选） 组装*elsestatements*如果上一个表达式为 false。 请注意，在程序集时计算这些表达式。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>