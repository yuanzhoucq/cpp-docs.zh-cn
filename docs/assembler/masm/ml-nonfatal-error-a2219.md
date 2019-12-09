---
title: ML 非致命错误 A2219
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: cf2be5db2aa9c21597c199a6840f4aaa50e0a681
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854584"
---
# <a name="ml-nonfatal-error-a2219"></a>ML 非致命错误 A2219

> 展开代码中偏移量的错误对齐方式

## <a name="remarks"></a>备注

[&period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md)和[&period;SAVEREG](../../assembler/masm/dot-savereg.md)的操作数必须是8的倍数。  [&period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md)和[&period;.setframe](../../assembler/masm/dot-setframe.md)的操作数必须是16的倍数。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)
