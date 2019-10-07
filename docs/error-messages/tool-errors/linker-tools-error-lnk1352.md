---
title: 链接器工具错误 LNK1352
description: 如果尝试不受支持的节合并，则会出现链接器工具错误 LNK1352。
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908392"
---
# <a name="linker-tools-error-lnk1352"></a>链接器工具错误 LNK1352

> 无法将 "*section_name_1*" 和 "*section_name_2*" 合并到不同部分

## <a name="remarks"></a>备注

链接器检测到不允许的节合并，因为必须将*section_name_1*和*section_name_2*合并到同一个节。 例如，如果链接器检测到尝试将`.stls`节`.tls`和节合并到不同的节中，则会发生此错误。

### <a name="to-correct-this-error"></a>更正此错误

对于此问题，请检查链接器命令行上的[/merge](../../build/reference/merge-combine-sections.md)选项。

## <a name="see-also"></a>请参阅

[链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
