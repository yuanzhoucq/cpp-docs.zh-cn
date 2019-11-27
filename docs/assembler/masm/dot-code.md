---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: a5b6608ca71a2b406c54a06cd44ac2865211a8ac
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398583"
---
# <a name="code"></a>.CODE

与一起使用时[。模型](../../assembler/masm/dot-model.md)，指示代码段的开头。

## <a name="syntax"></a>语法

> **.CODE** ⟦*name*⟧

### <a name="parameters"></a>参数

*名称*\
可选参数，用于指定代码段的名称。 对于小型、小型、紧凑型和平面[模型](../../assembler/masm/dot-model.md)，默认名称是 **_TEXT** 。 对于其他模型，默认名称为*modulename*_TEXT。

## <a name="see-also"></a>另请参阅

[指令引用](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
