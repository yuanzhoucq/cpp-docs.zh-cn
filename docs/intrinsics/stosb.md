---
title: __stosb |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosb
dev_langs:
- C++
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61050f8fc1924f6d2a143893af5bd1918df94394
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895183"
---
# <a name="stosb"></a>__stosb

**Microsoft 专用**

生成的存储字符串指令 (`rep stosb`)。

## <a name="syntax"></a>语法

```
void __stosb(
   unsigned char* Dest,
   unsigned char Data,
   size_t Count
);
```

#### <a name="parameters"></a>参数

[out] `Dest`  
该操作的目标。

[in] `Data`  
要存储的数据。

[in] `Count`  
要写入的字节块的长度。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__stosb`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

结果是，字符`Data`写入到块`Count`中的字节`Dest`字符串。

此例程仅可用作内部函数。

## <a name="example"></a>示例

```C
// stosb.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosb)  

int main()  
{
    unsigned char c = 0x40; /* '@' character */
    unsigned char s[] = "*********************************";

    printf_s("%s\n", s);
    __stosb((unsigned char*)s+1, c, 6);
    printf_s("%s\n", s);

}
```  

```Output
*********************************  
*@@@@@@**************************  
```  

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)