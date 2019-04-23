---
title: __outbytestring
ms.date: 11/04/2016
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 41064dda6a1a0b9ad4c15f98c3f3081f08ef8db6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032188"
---
# <a name="outbytestring"></a>__outbytestring

**Microsoft 专用**

将生成`rep outsb`指令，将发送第一个`Count`指向的数据的字节`Buffer`到指定的端口`Port`。

## <a name="syntax"></a>语法

```
void __outbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要向其发送数据的端口。

*Buffer*<br/>
[in]要指定的端口发送的数据。

“计数”<br/>
[in]要发送的数据的字节数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outbytestring`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)