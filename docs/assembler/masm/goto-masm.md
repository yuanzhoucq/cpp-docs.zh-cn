---
title: GOTO (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0be678e2d39389cbc551c386c1890f799124b5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43694009"
---
# <a name="goto-masm"></a>GOTO (MASM)

将程序集传输到标记的行 **:**_macrolabel_。

## <a name="syntax"></a>语法

> **GOTO** *macrolabel*

## <a name="remarks"></a>备注

**GOTO**仅在内允许[宏](macro.md)，[有关](for-masm.md)， [FORC](forc.md)，[重复](repeat.md)，和[时](while-masm.md)块。 *Macrolabel*目标必须是在行上唯一的指令，并且必须前面加前导冒号。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>
