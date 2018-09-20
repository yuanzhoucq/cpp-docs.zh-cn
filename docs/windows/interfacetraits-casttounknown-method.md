---
title: 'Interfacetraits:: Casttounknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c75e02136c626d72215a2af79d1391863e9f494c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382657"
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数的类型*ptr*。

*ptr*<br/>
指向类型的指针*T*。

## <a name="return-value"></a>返回值

从其指向 IUnknown 的指针`Base`派生。

## <a name="remarks"></a>备注

将转换为指针指定的指针`IUnknown`。

有关详细信息`Base`，请参阅中的公共 Typedef 部分[InterfaceTraits 结构](../windows/interfacetraits-structure.md)。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[InterfaceTraits 结构](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)