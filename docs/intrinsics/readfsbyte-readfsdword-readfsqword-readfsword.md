---
title: __readfsbyte、__readfsdword、__readfsqword、__readfsword
ms.date: 11/04/2016
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: bbf963d3a7b927d46485465a61fa08328b8efb52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507979"
---
# <a name="readfsbyte-readfsdword-readfsqword-readfsword"></a>__readfsbyte、__readfsdword、__readfsqword、__readfsword

**Microsoft 专用**

从指定相对于 FS 段的开头的偏移量的位置读取内存。

## <a name="syntax"></a>语法

```
unsigned char __readfsbyte( 
   unsigned long Offset 
);
unsigned short __readfsword( 
   unsigned long Offset 
);
unsigned long __readfsdword( 
   unsigned long Offset
);
unsigned __int64 __readfsqword( 
   unsigned long Offset 
);
```

#### <a name="parameters"></a>参数

*偏移量*<br/>
[in]从开始处的偏移量`FS`读取。

## <a name="return-value"></a>返回值

内存内容的字节、 字、 双字或四字 （如所示的调用的函数名称） 的位置`FS:[Offset]`。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

这些例程只能用作内部函数可使用。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__writefsbyte， \__writefsdword， \__writefsqword， \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)