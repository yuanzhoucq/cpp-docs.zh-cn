---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 469b49832c171ee78336a0c457f0d269acd3b59d
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397532"
---
# <a name="externdef"></a>EXTERNDEF

定义一个或多个名为*type* *类型的外部*变量、标签或符号。

## <a name="syntax"></a>语法

> **EXTERNDEF** ⟦*language-type*⟧ *name* __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* __：__ *type* .。。⟧

## <a name="remarks"></a>备注

如果*名称*是在模块中定义的，则将其视为[公共](../../assembler/masm/public-masm.md)的。 如果在模块中引用名称，则该*名称*将被视为[EXTERN](../../assembler/masm/extern-masm.md)。 如果未引用*名称*，则忽略它。 该*类型*可以是[ABS](../../assembler/masm/operator-abs.md)，后者将*名称*导入为常量。 通常在包含文件中使用。

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
