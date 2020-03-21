---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076267"
---
# <a name="code"></a>.CODE

（仅限32位 MASM。）与一起使用时[。模型](dot-model.md)，指示代码段的开头。

## <a name="syntax"></a>语法

> **.CODE** ⟦*name*⟧ \
> ⟦ *segmentItem* ⟧ ... \
> ⟦ *codesegmentnameId* **结束**;⟧\

### <a name="parameters"></a>parameters

*名称*\
可选参数，用于指定代码段的名称。 对于小型、小型、紧凑型和平面[模型](dot-model.md)，默认名称是 **_TEXT** 。 对于其他模型，默认名称为*modulename*_TEXT。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[.数据](dot-data.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
