---
title: __incgsbyte, __incgsword, __incgsdword, __incgsqword
ms.date: 11/04/2016
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
ms.openlocfilehash: c0fb12a56a8c6e0220818d54ee5ec7413fe56b43
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220252"
---
# <a name="incgsbyte-incgsword-incgsdword-incgsqword"></a>__incgsbyte, __incgsword, __incgsdword, __incgsqword

**Microsoft 专用**

指定相对于开头的偏移量的内存位置中添加一个值`GS`段。

## <a name="syntax"></a>语法

```
void __incgsbyte(
   unsigned long Offset
);
void __incgsword(
   unsigned long Offset
);
void __incgsdword(
   unsigned long Offset
);
void __incgsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>参数

*偏移量*<br/>
[in]从开始处的偏移量`GS`。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__incgsbyte`|X64|
|`__incgsword`|X64|
|`__incgsdword`|X64|
|`__incgsqword`|X64|

## <a name="remarks"></a>备注

这些例程都仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__addgsbyte， \__addgsword， \__addgsdword， \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)<br/>
[__readgsbyte， \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)<br/>
[__writegsbyte， \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[编译器内部函数](../intrinsics/compiler-intrinsics.md)
