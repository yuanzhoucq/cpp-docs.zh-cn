---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: a03cbda5a8ff64f6c167766f416e7744a5382ad5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203073"
---
# <a name="goto-masm"></a>GOTO (MASM)

将程序集传输到标记的行 **:**_macrolabel_。

## <a name="syntax"></a>语法

> **GOTO** *macrolabel*

## <a name="remarks"></a>备注

**GOTO**仅在内允许[宏](macro.md)，[有关](for-masm.md)， [FORC](forc.md)，[重复](repeat.md)，和[时](while-masm.md)块。 *Macrolabel*目标必须是在行上唯一的指令，并且必须前面加前导冒号。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>
