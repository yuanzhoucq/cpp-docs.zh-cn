---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 6992ec8b151a83b3f9fa920997845c20caf0476d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317742"
---
# <a name="if-32-bit-masm"></a>.IF （32位 MASM）

生成测试*condition1*的代码（例如，AX > 7），如果该条件为 true，则执行*语句*。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **.如果** *condition1*\
> *语句*\
> ⟦ **。ELSEIF** *condition2*\
> *语句*⟧ \
> ⟦ **。ELSE**\
> *语句*⟧ \
> **.ENDIF**

## <a name="remarks"></a>备注

如果为[。否则](dot-else.md)，如果原始条件为 false，则执行其语句。 请注意，将在运行时评估条件。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
