---
title: __indwordstring
ms.date: 11/04/2016
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: 96ad1551eb51ab1a91127cf57c9bd7915b84c379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574389"
---
# <a name="indwordstring"></a>__indwordstring

**Microsoft 专用**

从指定的端口使用读取数据`rep insd`指令。

## <a name="syntax"></a>语法

```
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要读取的端口。

*Buffer*<br/>
[out]读取从端口将数据写入此处。

“计数”<br/>
[in]要读取的数据的字节数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__indwordstring`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)