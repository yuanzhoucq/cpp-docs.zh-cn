---
title: 'Runtimeclassbaset:: Asiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b50466fc2c357c1d57fca272ff343cd56f3689c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604261"
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>参数

*T*  
实现接口 ID 由参数指定的类型*riid*。

*实现*  
指定模板参数的类型的变量*T*。

*riid*  
要检索的接口 ID。

*ppvObject*  
如果此操作成功，由参数指定指针-到-a-指向接口的指针*riid*。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

## <a name="remarks"></a>备注

检索指向指定的接口 id。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[RuntimeClassBaseT 结构](../windows/runtimeclassbaset-structure.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)