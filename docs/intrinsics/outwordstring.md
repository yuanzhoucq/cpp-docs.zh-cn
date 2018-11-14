---
title: __outwordstring
ms.date: 11/04/2016
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: df7ca6ddbb80c21397beb91b8e671f248f2a1d9c
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326285"
---
# <a name="outwordstring"></a>__outwordstring

**Microsoft 专用**

将生成`rep outsw`指令，将发送`Count`处开头的单词`Buffer`出指定的 I/O 端口`Port`。

## <a name="syntax"></a>语法

```
void __outwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>参数

*端口*<br/>
[in]要向其发送数据的端口。

*Buffer*<br/>
[in]指向要指定的端口发送的数据的指针。

“计数”<br/>
[in]若要发送的单词数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__outwordstring`|x86、x64|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

此例程仅可用作内部函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)