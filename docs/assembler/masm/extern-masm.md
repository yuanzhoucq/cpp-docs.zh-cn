---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: fc66338d90b54ecb12ef3ab1aa56214fb445cb13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397568"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定义一个或多个名为*type* *类型的外部*变量、标签或符号。

## <a name="syntax"></a>语法

> **EXTERN** ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* .。。⟧

## <a name="remarks"></a>备注

该*类型*可以是[ABS](../../assembler/masm/operator-abs.md)，后者将*名称*导入为常量。 与[EXTRN](../../assembler/masm/extrn.md)相同。

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
