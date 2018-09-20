---
title: 'Comptrref:: Getaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 797df323-a2fa-412b-ab60-32cce3721096
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a0f35bbe2bdc0d0c8d3500e6b157da542458b1fe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421007"
---
# <a name="comptrrefgetaddressof-method"></a>ComPtrRef::GetAddressOf 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
InterfaceType* const * GetAddressOf() const;
```

## <a name="return-value"></a>返回值

指向当前所表示接口的指针的地址**ComPtrRef**对象。

## <a name="remarks"></a>备注

检索指向当前所表示接口的指针的地址**ComPtrRef**对象。

## <a name="requirements"></a>要求

**标头：** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[ComPtrRef 类](../windows/comptrref-class.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)