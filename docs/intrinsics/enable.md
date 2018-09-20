---
title: 启用 （_e) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _enable
- _enable_cpp
dev_langs:
- C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3b59bc6665c4622078285a0c3b4b5011bc7d9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433369"
---
# <a name="enable"></a>_enable

**Microsoft 专用**

启用中断。

## <a name="syntax"></a>语法

```
void _enable(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_enable`|x86、 ARM、 x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

`_enable` 指示处理器设置中断标志。 在 x86 系统上，此函数会生成“设置中断标志”(`sti`) 指令。

此函数只有在内核模式下才可用。 如果在用户模式下使用，会引发特权指令异常。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)