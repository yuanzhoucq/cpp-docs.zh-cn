---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: 9e726413f0bbfbd9d6affa348777c995c51283a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245505"
---
# <a name="jitintrinsic"></a>jitintrinsic

将函数标记为对 64 位公共语言运行时很有用。 这用于 Microsoft 提供的库中的某些函数。

## <a name="syntax"></a>语法

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>备注

**jitintrinsic**添加 MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 到函数签名。

禁止用户使用此 **__declspec**修饰符，意外的结果作为可以发生。

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)