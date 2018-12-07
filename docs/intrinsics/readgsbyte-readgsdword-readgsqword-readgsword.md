---
title: __readgsbyte、__readgsdword、__readgsqword、__readgsword
ms.date: 11/04/2016
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: 1bc6a3b2ef2d78e5b30ea36149ea691468c9b0ec
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327507"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte、__readgsdword、__readgsqword、__readgsword

**Microsoft 专用**

从指定相对于 GS 段开头的偏移量的位置读取内存。

## <a name="syntax"></a>语法

```
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>参数

*偏移量*<br/>
[in]从开始处的偏移量`GS`读取。

## <a name="return-value"></a>返回值

内存内容的字节、 字、 双字或四字 （如所示的调用的函数名称） 的位置`GS:[Offset]`。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

这些内部函数只有在内核模式下可用，例程都仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__writegsbyte， \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)