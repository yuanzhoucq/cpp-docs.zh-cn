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
ms.openlocfilehash: 80af8f463d6cd1af631c6cb37c0239e7a9e85c3f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595880"
---
# <a name="hstringhstring-constructor"></a>HString::HString 构造函数

初始化的新实例**HString**类。

## <a name="syntax"></a>语法

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>参数

*hstr*  
HSTRING 句柄。

*other*  
将现有**HString**对象。

## <a name="remarks"></a>备注

第一个构造函数初始化新**HString**对象为空。

第二个构造函数初始化新**HString**对象的现有值*其他*参数，然后再销毁*其他*参数。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)