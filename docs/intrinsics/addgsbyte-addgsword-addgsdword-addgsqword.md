---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword
ms.date: 11/04/2016
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
ms.openlocfilehash: 2439e541332705ec5330a7ee6e703c99712f7e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667595"
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword

**Microsoft 专用**

将值添加到指定相对于开头的偏移量的内存位置`GS`段。

## <a name="syntax"></a>语法

```
void __addgsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __addgsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __addgsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
void __addgsqword( 
   unsigned long Offset, 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>参数

*偏移量*<br/>
[in]从开始处的偏移量`GS`。

*Data*<br/>
[in]要添加到内存位置的值。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__addgsbyte`|X64|
|`__addgsword`|X64|
|`__addgsdword`|X64|
|`__addgsqword`|X64|

## <a name="remarks"></a>备注

这些内部函数可用于在内核模式下，并且这些例程仅用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__incgsbyte， \__incgsword， \__incgsdword， \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)<br/>
[__readgsbyte， \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[__writegsbyte， \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)