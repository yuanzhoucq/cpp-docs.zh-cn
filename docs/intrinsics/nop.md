---
title: __nop
ms.date: 11/04/2016
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 25ba27485990ceaae77e1827f0c74680914e2f40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651719"
---
# <a name="nop"></a>__nop

**Microsoft 专用**

生成特定于平台的机器代码，会执行任何操作。

## <a name="syntax"></a>语法

```
void __nop();
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__nop`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="remarks"></a>备注

`__nop` 函数等同于 `NOP` 计算机指令。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，2 卷： 指令集引用"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)