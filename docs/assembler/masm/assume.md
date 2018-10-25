---
title: 假定 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6fbba50e56ae06dc3afb64582d4a131bba75a6c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055848"
---
# <a name="assume"></a>ASSUME

启用错误检查寄存器的值。

## <a name="syntax"></a>语法

> 假设*segregister*:*名称*[[， *segregister*:*名称*]]...<br/>
> 假设*dataregister*:*类型*[[， *dataregister*:*类型*]]...<br/>
> 假设*注册*： 错误 [[，*注册*： 错误]]...<br/>
> 假设 [[*注册*:]] 执行任何操作 [[，*注册*： 执行任何操作]]...

## <a name="remarks"></a>备注

之后`ASSUME`放入的效果，则组装器会监视对给定的寄存器的值进行更改。 **错误**如果使用寄存器，将生成错误。 **执行任何操作**删除注册的错误检查。 你可以组合不同种类的假设在一个语句中。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>