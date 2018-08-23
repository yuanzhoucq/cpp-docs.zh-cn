---
title: 'Runtimeclass:: Getiids 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3c16d54b08d0c687b33381107eb17be351e9d6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589477"
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids 方法

获取一个数组，其中可以包含的接口 Id 由当前**RuntimeClass**对象。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   GetIids
)  
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>参数

*iidCount*  
此操作完成后，数组中的元素总数*iid*。

*iid*  
此操作完成后，指向接口 ID 数组的指针。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 E_OUTOFMEMORY。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[RuntimeClass 类](../windows/runtimeclass-class.md)