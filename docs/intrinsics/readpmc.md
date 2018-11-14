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
ms.openlocfilehash: 059d9344fa329e69666abaca4d73122ab29f8d2a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326428"
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