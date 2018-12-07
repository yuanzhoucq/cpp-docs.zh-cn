---
title: __writecr0
ms.date: 11/04/2016
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: cdc93f178f033b072cad68180dfee305d9bf62a5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330523"
---
# <a name="writecr0"></a>__writecr0

**Microsoft 专用**

将值写入`Data`到 CR0 寄存器。

## <a name="syntax"></a>语法

```
void writecr0(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>参数

*Data*<br/>
[in]要写入到 CR0 寄存器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writecr0`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数只在内核模式下可用，例程只能用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)