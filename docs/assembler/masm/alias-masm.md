---
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 5aef169c5632e74722438c63718ce5b783a8da09
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316598"
---
# <a name="alias"></a>ALIAS

**ALIAS**指令创建函数的替代名称。  这允许您为函数创建多个名称，或创建允许链接器（LINK）将旧函数映射到新函数的库。

## <a name="syntax"></a>语法

> **别名 \<** _别名_ **> = \<** _实际名称_ **>**

#### <a name="parameters"></a>参数

*实际名称*\
函数或过程的实际名称。  尖括号是必需的。

*别名*\
备用或别名。  尖括号是必需的。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
