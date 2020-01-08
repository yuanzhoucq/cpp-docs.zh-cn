---
title: IF1 和 IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: 60f8b0dcedb61ac06de929aff300845e342d7cfc
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317313"
---
# <a name="if1-and-if2"></a>IF1 和 IF2

在第一个程序集通过时计算**IF1**块。

如果**选项： SETIF2**为**TRUE**，则对每个程序集 pass 计算**IF2**块。

## <a name="syntax"></a>语法

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>备注

[若](if-masm.md)要获取完整的语法，请参阅。

不同于版本5.1，MASM 6.1 和更高版本在第一次传递时执行其大部分工作，然后根据需要执行任意数量的后续处理。 与此相反，MASM 5.1 始终在两个源阶段内装配。 因此，您可能需要在 MASM 6.1 和更高版本下修改或删除某些依赖于依赖关系的构造。

### <a name="two-pass-directives"></a>双重传递指令

为了确保兼容性，MASM 6.1 和更高版本支持引用两个阶段的5.1 指令。 其中包括 **。ERR1**、 **。ERR2**、 **IF1**、 **IF2**、 **ELSEIF1**和**ELSEIF2**。 对于第二遍构造，必须指定[选项 SETIF2](option-masm.md)。 如果没有**选项 SETIF2**，则**IF2**和 **。ERR2**指令导致错误：

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6.1 及更高版本以不同方式处理第一遍构造。 它处理 **。ERR1**指令视为 **。ERR**和**IF1** **指令。**

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
