---
title: __inwordstring
ms.date: 09/02/2019
f1_keywords:
- __inwordstring
- __inwordstring_cpp
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
ms.openlocfilehash: a6f67e15bc5eef9fbe9cc8d12e95afcdf869e3b1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221876"
---
# <a name="__inwordstring"></a>__inwordstring

**Microsoft 专用**

使用`rep insw`指令从指定端口读取数据。

## <a name="syntax"></a>语法

```C
void __inwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>参数

*口*\
中要从其读取的端口。

*宽限*\
弄此处写入从端口读取的数据。

*计*\
中要读取的数据的字数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__inwordstring`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
