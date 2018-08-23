---
title: 'Interfacetraits:: Casttobase 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55a4d7487be5b3565ba3945630cab4388f287a68
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611819"
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*  
参数的类型*ptr*。

*ptr*  
指向类型指针*T*。

## <a name="return-value"></a>返回值

一个指向`Base`。

## <a name="remarks"></a>备注

将转换为指针指定的指针`Base`。

有关详细信息`Base`，请参阅中的公共 Typedef 部分[InterfaceTraits 结构](../windows/interfacetraits-structure.md)。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[InterfaceTraits 结构](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)