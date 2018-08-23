---
title: 'Hstring:: Getaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e327e2818903396c154be7406ec325695b6b6982
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613360"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf 方法

检索指向基础 HSTRING 句柄。

## <a name="syntax"></a>语法

```cpp
HSTRING* GetAddressOf() throw()  
```

## <a name="return-value"></a>返回值

指向基础 HSTRING 句柄的指针。

## <a name="remarks"></a>备注

此操作后，将销毁基础 HSTRING 句柄的字符串值。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HString 类](../windows/hstring-class.md)