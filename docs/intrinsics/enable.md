---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: e1ece6d6f4040b81b55d8400407d46f165b56b53
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024512"
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