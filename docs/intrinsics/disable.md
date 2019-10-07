---
title: _disable
ms.date: 09/02/2019
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 94be850e1d494ff62df84922b46f28481be68314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216817"
---
# <a name="_disable"></a>_disable

**Microsoft 专用**

禁用中断。

## <a name="syntax"></a>语法

```C
void _disable(void);
```

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`_disable`|x86、ARM、x64、ARM64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

`_disable` 指示处理器去清除中断标记。 在 x86 系统上，此函数会生成“清除中断标记”(`cli`) 指令。

此函数只有在内核模式下才可用。 如果在用户模式下使用，运行时会出现特权指令异常。

在 ARM 和 ARM64 平台上, 此例程仅作为内部函数提供。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
