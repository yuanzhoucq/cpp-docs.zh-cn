---
title: __indword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: f4b37247093da14c8d5e8fed69b01265d3fed2ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599805"
---
# <a name="indword"></a>__indword

**Microsoft 专用**

从指定的端口使用读取的数据的一个双字`in`指令。

## <a name="syntax"></a>语法

```
unsigned long __indword(
   unsigned short Port
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要读取的端口。

## <a name="return-value"></a>返回值

从端口读取单词。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__indword`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)