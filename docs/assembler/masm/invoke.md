---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 853bc9cd22d866357a4cd2d695beccc3efc20acf
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703958"
---
# <a name="invoke-32-bit-masm"></a>INVOKE （32位 MASM）

调用由*expression*给定的地址处的过程，并根据语言类型的标准调用约定在堆栈上或在寄存器中传递参数。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> INVOKE*表达式*[[， *arguments*]]

## <a name="remarks"></a>备注

传递给过程的每个参数可以是表达式、寄存器对或地址表达式（前面带有 `ADDR`的表达式）。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>