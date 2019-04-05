---
title: __movsb
ms.date: 11/04/2016
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 42124743c27b297c723780c1bc19038fb54e638d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024989"
---
# <a name="movsb"></a>__movsb

**Microsoft 专用**

生成移动字符串 (`rep movsb`) 指令。

## <a name="syntax"></a>语法

```
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>参数

*目标*<br/>
[out]一个指向该副本的目标。

*源*<br/>
[in]指向源的副本的指针。

*计数*<br/>
[in]要复制的字节数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__movsb`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

结果是，第一个`Count`指向字节`Source`复制到`Destination`字符串。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)