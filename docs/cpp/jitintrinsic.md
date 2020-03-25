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
ms.openlocfilehash: 4626ba82d1d24582951bbffd8e6be687007d390f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178169"
---
# <a name="jitintrinsic"></a>jitintrinsic

将函数标记为对 64 位公共语言运行时很有用。 这用于 Microsoft 提供的库中的某些函数。

## <a name="syntax"></a>语法

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>备注

**jitintrinsic**将 MODOPT （<xref:System.Runtime.CompilerServices.IsJitIntrinsic>）添加到函数签名。

不鼓励用户使用此 **__declspec**修饰符，因为可能会发生意外的结果。

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
