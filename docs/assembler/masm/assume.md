---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 73ef8bcc33087a56747b80f94482fcd6c50e3bf6
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399266"
---
# <a name="assume-32-bit-masm"></a>假设（32位 MASM）

启用寄存器值的错误检查。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **假定**  *segregister* __：__ *name* ⟦ __，__ *segregister* __：__ *name*.。。⟧\
> **假定**  *dataregister* __：__ *type* ⟦ __，__ *dataregister* __：__ *type*.。。⟧\
> **假设**  *注册* __：错误__⟦ __，__ *注册* __：错误__.。。⟧\
> **假设**⟦*register* __：__ ⟧**NOTHING** ⟦ __，__ *register* __： nothing__⟧

## <a name="remarks"></a>备注

**假设**生效后，汇编程序会监视给定寄存器值的更改。 如果使用了寄存器，则**错误**将生成错误。 不**会删除注册**错误检查。 可以在一个语句中组合不同种类的假设。

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
