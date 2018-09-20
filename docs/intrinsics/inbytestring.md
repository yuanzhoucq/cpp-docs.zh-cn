---
title: __inbytestring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inbytestring
- __inbytestring_cpp
dev_langs:
- C++
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e8b2fc0420862be3dd46eca09614ded57f06b7e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372259"
---
# <a name="inbytestring"></a>__inbytestring

**Microsoft 专用**

从指定的端口使用读取数据`rep insb`指令。

## <a name="syntax"></a>语法

```
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
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
|`__inbytestring`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)