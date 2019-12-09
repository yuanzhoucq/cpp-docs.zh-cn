---
title: ML 错误 A1008
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1008
helpviewer_keywords:
- A1008
ms.assetid: fe592f9d-c37b-4cd8-a51d-e3c15ddcab83
ms.openlocfilehash: 19b1aa5bdc5f3b254cf87840bbf6fabb03c18ada
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856886"
---
# <a name="ml-fatal-error-a1008"></a>ML 错误 A1008

**不匹配的宏嵌套**

宏在文件末尾之前未终止，或在宏块外发现了终止指令[ENDM](../../assembler/masm/endm.md) 。

此错误的一个原因就是在之前省略点[。重复](../../assembler/masm/dot-repeat.md)或[。WHILE](../../assembler/masm/dot-while.md)。

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>