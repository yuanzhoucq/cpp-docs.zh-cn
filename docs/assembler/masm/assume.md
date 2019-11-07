---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 4bf8f0c41e9ce3e296cf201efd4fd9be2033cbdb
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73702471"
---
# <a name="assume-32-bit-masm"></a>假设（32位 MASM）

启用寄存器值的错误检查。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> 假定*segregister*：*name* [[， *segregister*：*name*]] 。<br/>
> 假定*dataregister*：*type* [[， *dataregister*：*type*]] 。<br/>
> 假设*注册*： error [[， *register*： error]] 。<br/>
> 假设 [[*register*：]] 没有 [[， *register*： NOTHING]] 。

## <a name="remarks"></a>备注

在 `ASSUME` 生效后，汇编程序会监视给定寄存器值的更改。 如果使用了寄存器，则**错误**将生成错误。 不**会删除注册**错误检查。 可以在一个语句中组合不同种类的假设。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>