---
title: 'Interfacetraits:: Cancastto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aea326149c9748ff480d523a1078f54ba733cb14
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610415"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*ptr*  
指向类型的名称。

*riid*  
接口 ID `Base`。

*ppv*  
如果此操作成功， *ppv*指向由指定的界面`Base`。 否则为*ppv*设置为**nullptr**。

## <a name="return-value"></a>返回值

**true**此操作是否成功并*ptr*被强制转换为一个指向`Base`; 否则为**false** 。

## <a name="remarks"></a>备注

指示是否指定的指针可以转换为一个指向`Base`。

有关详细信息`Base`，请参阅**公共 Typedef**主题中[InterfaceTraits 结构](../windows/interfacetraits-structure.md)。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[InterfaceTraits 结构](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)