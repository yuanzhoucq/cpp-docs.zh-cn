---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 274ac451005015b2693d8674673af574ec781bdc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399294"
---
# <a name="alias-masm"></a>ALIAS (MASM)

**ALIAS**指令创建函数的替代名称。  这允许您为函数创建多个名称，或创建允许链接器（LINK）将旧函数映射到新函数的库。

## <a name="syntax"></a>语法

> **别名 \<** _别名_ **> = \<** _实际名称_ **>**

#### <a name="parameters"></a>参数

*实际名称*\
函数或过程的实际名称。  尖括号是必需的。

*别名*\
备用或别名。  尖括号是必需的。

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
