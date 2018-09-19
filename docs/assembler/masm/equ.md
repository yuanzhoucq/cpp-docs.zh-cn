---
title: EQU |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EQU
dev_langs:
- C++
helpviewer_keywords:
- EQU directive
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37509a39d2247649c2971932f402a18f3ac667d4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681302"
---
# <a name="equ"></a>EQU

第一个指令将分配数值*表达式*到*名称*。

## <a name="syntax"></a>语法

> *名称*EQU*表达式*

> *名称*EQU \<*文本*>

## <a name="remarks"></a>备注

*名称*更高版本不能重新定义。

指定第二个指令分配*文本*到*名称*。 *名称*可以分配不同*文本*更高版本。 请参阅[TEXTEQU](../../assembler/masm/textequ.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>