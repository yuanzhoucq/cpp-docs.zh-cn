---
title: __outword
ms.date: 09/02/2019
f1_keywords:
- __outword
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
ms.openlocfilehash: 766f6adff5ea0212f48ff8727024ac7a5729c944
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221400"
---
# <a name="__outword"></a>__outword

**Microsoft 专用**

生成指令, 该指令将向外发送由*端口*指定的 i/o 端口的单词。 `out`

## <a name="syntax"></a>语法

```C
void __outword(
   unsigned short Port,
   unsigned short Data
);
```

### <a name="parameters"></a>参数

*口*\
中要将数据发送到的端口。

*数据*\
中要发送的数据。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outword`|x86、x64|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
