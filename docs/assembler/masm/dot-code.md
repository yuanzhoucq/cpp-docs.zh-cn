---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 0975e96e670400b7fa221ae2d1b9982b5cee613b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314141"
---
# <a name="code"></a>.CODE

（仅限32位 MASM。）与一起使用时[。模型](dot-model.md)，指示代码段的开头。

## <a name="syntax"></a>语法

> **.CODE** ⟦*name*⟧ \
> ⟦ *segmentItem* ⟧ ... \
> ⟦ *codesegmentnameId* **结束**;⟧\

### <a name="parameters"></a>参数

*名称*\
可选参数，用于指定代码段的名称。 对于小型、小型、紧凑型和平面[模型](dot-model.md)，默认名称是 **_TEXT** 。 对于其他模型，默认名称为*modulename*_TEXT。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[.数据](dot-data.md)\
[MASM BNF 语法](masm-bnf-grammar.md)

