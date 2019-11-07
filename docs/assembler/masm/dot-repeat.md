---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 0533397c60c83f22b10c84ec72aa6eb65a71e4c0
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703572"
---
# <a name="repeat-32-bit-masm"></a>.重复（32位 MASM）

生成重复执行*语句*块的代码，直到 `condition` 变成 true。 [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md)，当 CX 为零时，这将变为 true，可以替换为[。直到](../../assembler/masm/dot-until.md)。 `condition` 在中是可选的 **.UNTILCXZ**。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> .REPEAT<br/>
> 语句<br/>
> .截止时间

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>