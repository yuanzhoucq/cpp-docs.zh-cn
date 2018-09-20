---
title: __stosw |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosw
dev_langs:
- C++
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41f086c2427d8147014bb6df25f3923d3ab4b84c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401324"
---
# <a name="stosw"></a>__stosw

**Microsoft 专用**

生成的存储字符串指令 (`rep stosw`)。

## <a name="syntax"></a>语法

```
void __stosw( 
   unsigned short* Dest, 
   unsigned short Data, 
   size_t Count 
);
```

#### <a name="parameters"></a>参数

*dest*<br/>
[out]该操作的目标。

*Data*<br/>
[in]要存储的数据。

“计数”<br/>
[in]中的单词写入块的长度。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__stosw`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

结果是，字`Data`写入到块`Count`词中`Dest`字符串。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)