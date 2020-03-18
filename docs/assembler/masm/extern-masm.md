---
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 2674f358fe22f74c5272d90a0d8cbff234ddcd11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440881"
---
# <a name="extern"></a>EXTERN

定义一个或多个名为*type* *类型的外部*变量、标签或符号。

## <a name="syntax"></a>语法

> **EXTERN** ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* ⟦ __（__ *altid* __）__ ⟧ __：__ *type* .。。⟧

## <a name="remarks"></a>备注

*语言类型*参数仅在32位 MASM 中有效。

该*类型*可以是[ABS](operator-abs.md)，后者将*名称*导入为常量。 与[EXTRN](extrn.md)相同。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
