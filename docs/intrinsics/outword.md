---
title: __outword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outword
dev_langs:
- C++
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eac50ba9c4c1b4bc14ebb847b283b5c2da11605e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388793"
---
# <a name="outword"></a>__outword

**Microsoft 专用**

将生成`out`指令，将发送一词`Data`出指定的 I/O 端口`Port`。

## <a name="syntax"></a>语法

```
void __outword( 
   unsigned short Port, 
   unsigned short Data 
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要向其发送数据的端口。

*Data*<br/>
[in]要发送的数据。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outword`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)