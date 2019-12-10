---
title: .CODE
ms.date: 12/06/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 36d9c01d2a24b446ddc91fe73f3cb677067b3e4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987916"
---
# <a name="code-32-bit-masm"></a>.代码（32位 MASM）

与一起使用时[。模型](../../assembler/masm/dot-model.md)，指示代码段的开头。

## <a name="syntax"></a>语法

> **.CODE** ⟦*name*⟧

### <a name="parameters"></a>参数

*名称*\
可选参数，用于指定代码段的名称。 对于小型、小型、紧凑型和平面[模型](../../assembler/masm/dot-model.md)，默认名称是 **_TEXT** 。 对于其他模型，默认名称为*modulename*_TEXT。

## <a name="see-also"></a>另请参阅

[指令引用](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
