---
title: GOTO (MASM)
ms.date: 12/16/2019
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: f198658f9a4b85e0b5ec9b7a0c122241e57286f6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317274"
---
# <a name="goto"></a>GOTO

将程序集传输**到标记为**"_macrolabel_" 的行。

## <a name="syntax"></a>语法

> **转**到*macrolabel*

## <a name="remarks"></a>备注

仅允许在[宏](macro.md)、[FOR](for-masm.md)、[强制](forc.md)、[重复](repeat.md)和[WHILE](while-masm.md)块中使用GOTO。 *Macrolabel*目标必须是行上唯一的指令，并且必须以前导冒号开头。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
