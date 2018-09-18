---
title: jitintrinsic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 888ec19eaedf881fed97a14a7f3f8b5ee673ce7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056282"
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