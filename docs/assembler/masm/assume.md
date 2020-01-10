---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316533"
---
# <a name="assume"></a>ASSUME

启用寄存器值的错误检查。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **假定**  *segregister* __：__ *name* ⟦ __，__ *segregister* __：__ *name*.。。⟧\
> **假定**  *dataregister* __：__ *type* ⟦ __，__ *dataregister* __：__ *type*.。。⟧\
> **假设**  *注册* __：错误__⟦ __，__ *注册* __：错误__.。。⟧\
> **假设**⟦*register* __：__ ⟧**NOTHING** ⟦ __，__ *register* __： nothing__⟧

## <a name="remarks"></a>备注

**假设**生效后，汇编程序会监视给定寄存器值的更改。 如果使用了寄存器，则**错误**将生成错误。 不**会删除注册**错误检查。 可以在一个语句中组合不同种类的假设。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
