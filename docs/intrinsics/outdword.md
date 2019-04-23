---
title: __outdword
ms.date: 11/04/2016
f1_keywords:
- __outdword
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
ms.openlocfilehash: 236c4812f62cb092876b400051248425ee1b13e7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034217"
---
# <a name="outdword"></a>__outdword

**Microsoft 专用**

将生成`out`指令以将发送双字`Data`输出端口`Port`。

## <a name="syntax"></a>语法

```
void __outdword(
   unsigned short Port,
   unsigned long Data
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要向其发送数据的端口。

*Data*<br/>
[in]要发送双字。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outdword`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)