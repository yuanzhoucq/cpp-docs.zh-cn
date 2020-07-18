---
title: OPTION (MASM)
ms.date: 07/15/2020
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a614697a9d633628b02b59a7b810fa261887f859
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446432"
---
# <a name="option"></a>OPTION

启用和禁用组装器的功能。

## <a name="syntax"></a>语法

> **`OPTION`***选项-列表*

## <a name="remarks"></a>备注

可用选项包括：

:::row:::
   :::column span="":::
      **`CASEMAP`**<br/>**`DOTNAME`**<br/>**`NODOTNAME`**<br/>**`EMULATOR`**<br/>**`NOEMULATOR`**<br/>**`EPILOGUE`**<br/>**`EXPR16`**
   :::column-end:::
   :::column span="":::
      **`EXPR32`**<br/>**`LANGUAGE`**<br/>**`LJMP`**<br/>**`NOLJMP`**<br/>**`M510`**<br/>**`NOM510`**<br/>**`NOKEYWORD`**
   :::column-end:::
   :::column span="":::
      **`NOSIGNEXTEND`**<br/>**`OFFSET`**<br/>**`OLDMACROS`**<br/>**`NOOLDMACROS`**<br/>**`OLDSTRUCTS`**<br/>**`NOOLDSTRUCTS`**<br/>**`PROC`**
   :::column-end:::
   :::column span="":::
      **`PROLOGUE`**<br/>**`READONLY`**<br/>**`NOREADONLY`**<br/>**`SCOPED`**<br/>**`NOSCOPED`**<br/>**`SEGMENT`**<br/>**`SETIF2`**
   :::column-end:::
:::row-end:::

LANGUAGE 的语法为 **`OPTION LANGUAGE:`** _`x`_ ，其中是、、、、或中的 *`x`* 一个 **`C`** **`SYSCALL`** **`STDCALL`** **`PASCAL`** **`FORTRAN`** **`BASIC`** 。 **`SYSCALL`****`PASCAL`** **`FORTRAN`** 不支持、、和 **`BASIC`** [`.MODEL`](dot-model.md) **`FLAT`** 。

## <a name="see-also"></a>请参阅

[指令参考](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
