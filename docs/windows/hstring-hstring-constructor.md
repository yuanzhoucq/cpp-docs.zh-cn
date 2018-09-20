---
title: 'Hstring:: Hstring 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59ec7c1635b825cc300e28e5c02e2a3864a6c123
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442248"
---
# <a name="hstringhstring-constructor"></a>HString::HString 构造函数

初始化的新实例**HString**类。

## <a name="syntax"></a>语法

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>参数

*hstr*<br/>
HSTRING 句柄。

*other*<br/>
将现有**HString**对象。

## <a name="remarks"></a>备注

第一个构造函数初始化新**HString**对象为空。

第二个构造函数初始化新**HString**对象的现有值*其他*参数，然后再销毁*其他*参数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)