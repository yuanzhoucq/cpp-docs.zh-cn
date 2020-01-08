---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 2cc5884a7473da9175a6b6af4b4251314deffeb4
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313387"
---
# <a name="externdef"></a>EXTERNDEF

定义一个或多个名为*type* *类型的外部*变量、标签或符号。

## <a name="syntax"></a>语法

> **EXTERNDEF** ⟦*language-type*⟧ *name* __：__ *type* ⟦ __，__ ⟦*language-type*⟧ *name* __：__ *type* .。。⟧

## <a name="remarks"></a>备注

*语言类型*参数仅在32位 MASM 中有效。

如果*名称*是在模块中定义的，则将其视为[公共](public-masm.md)的。 如果在模块中引用名称，则该*名称*将被视为[EXTERN](extern-masm.md)。 如果未引用*名称*，则忽略它。 该*类型*可以是[ABS](operator-abs.md)，后者将*名称*导入为常量。 通常在包含文件中使用。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
