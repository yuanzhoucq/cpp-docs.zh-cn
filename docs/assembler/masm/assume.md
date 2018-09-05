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
ms.openlocfilehash: 8a0e43548292d2ffecbebdaead6aa12d6dacc352
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693803"
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