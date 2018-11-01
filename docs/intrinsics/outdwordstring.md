---
title: __outdwordstring
ms.date: 11/04/2016
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: d94db2f59f9a3a8074331054b04cef59cebac0dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502591"
---
# <a name="outdwordstring"></a>__outdwordstring

**Microsoft 专用**

将生成`rep outsd`指令，将发送`Count`双字数组开始`Buffer`出指定的 I/O 端口`Port`。

## <a name="syntax"></a>语法

```
void __outdwordstring( 
   unsigned short Port, 
   unsigned long* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要向其发送数据的端口。

*Buffer*<br/>
[in]指向要指定的端口发送的数据的指针。

“计数”<br/>
[in]双字数组发送的数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outdwordstring`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)