---
title: __nop |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __nop
dev_langs:
- C++
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc5dab4ba2c23f60eb4407548cea5c15106c1401
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820491"
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

`__nop`函数等同于`NOP`计算机指令。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，2 卷： 指令集引用"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)