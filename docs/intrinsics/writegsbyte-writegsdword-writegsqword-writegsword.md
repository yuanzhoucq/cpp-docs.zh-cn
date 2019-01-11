---
title: __writegsbyte, __writegsdword, __writegsqword, __writegsword
ms.date: 11/04/2016
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
ms.openlocfilehash: 9276c727d93491e3d85cbae26f6b3df9c0384c59
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220239"
---
# <a name="writegsbyte-writegsdword-writegsqword-writegsword"></a>__writegsbyte, __writegsdword, __writegsqword, __writegsword

**Microsoft 专用**

内存写入指定相对于 GS 段开头的偏移量的位置。

## <a name="syntax"></a>语法

```
void __writegsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writegsword(
   unsigned long Offset,
   unsigned short Data
);
void __writegsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writegsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>参数

*偏移量*<br/>
[in]从要写入到的 GS 开头的偏移量。

*Data*<br/>
[in]要写入的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__writegsbyte`|X64|
|`__writegsdword`|X64|
|`__writegsqword`|X64|
|`__writegsword`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

这些例程都仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__readgsbyte， \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
