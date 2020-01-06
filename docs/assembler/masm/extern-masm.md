---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 38ea50e75f2a8e19a7a99860f691904053b6739a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987856"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定义一个或多个名为*type* *类型的外部*变量、标签或符号。

## <a name="syntax"></a>语法

> **EXTERN** ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* .。。⟧

## <a name="remarks"></a>备注

*语言类型*参数仅在32位 MASM 中有效。

该*类型*可以是[ABS](../../assembler/masm/operator-abs.md)，后者将*名称*导入为常量。 与[EXTRN](../../assembler/masm/extrn.md)相同。

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
