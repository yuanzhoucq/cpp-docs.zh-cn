---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: f21f3f3cc4cb86b1ca2503d515dcd7fbcdffe622
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318275"
---
# <a name="repeat-32-bit-masm"></a>.重复（32位 MASM）

生成重复执行*语句*块的代码，直到*condition*变为 true。 [.UNTILCXZ](dot-untilcxz.md)，当 CX 为零时，这将变为 true，可以替换为[。直到](dot-until.md)。 *条件*是可选的 **.UNTILCXZ**。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **.重复**\
> *语句*\
> **.截止**时间

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
