---
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 18f286d8634202b57dea788aa6984755a5afb197
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440798"
---
# <a name="goto"></a>GOTO

将程序集传输**到标记为**"_macrolabel_" 的行。

## <a name="syntax"></a>语法

> **转**到*macrolabel*

## <a name="remarks"></a>备注

仅允许在[宏](macro.md)、[强制](forc.md)、 [FOR](for-masm.md)[重复](repeat.md)和[WHILE](while-masm.md)块中使用**GOTO** 。 *Macrolabel*目标必须是行上唯一的指令，并且必须以前导冒号开头。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
