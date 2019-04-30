---
title: __readpmc
ms.date: 11/04/2016
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: 848c880e76d6d431ee56a0bb30a33b276837ce76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396439"
---
# <a name="readpmc"></a>__readpmc

**Microsoft 专用**

将生成`rdpmc`指令，读取性能监视计数器指定`counter`。

## <a name="syntax"></a>语法

```
unsigned __int64 __readpmc(
   unsigned long counter
);
```

#### <a name="parameters"></a>参数

*counter*<br/>
[in]要读取的性能计数器。

## <a name="return-value"></a>返回值

指定的性能计数器的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readpmc`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此内部函数现已推出，内核模式且例程仅用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)