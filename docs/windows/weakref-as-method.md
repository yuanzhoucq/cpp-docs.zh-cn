---
title: 'Weakref:: As 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2a56904fb3709137c167513d0eba426bda7ad14
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589364"
---
# <a name="weakrefas-method"></a>WeakRef::As 方法

设置指定`ComPtr`指针参数以表示指定的接口。

## <a name="syntax"></a>语法

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>参数

*U*  
接口 ID。

*ptr*  
此操作完成后，一个对象，表示参数*U*。

## <a name="return-value"></a>返回值

- 如果此操作成功，则为 S_OK否则，一个 HRESULT，指示的原因，操作失败，并*ptr*设置为**nullptr**。

- 如果此操作成功，但当前为 S_OK **WeakRef**已释放对象。 参数*ptr*设置为**nullptr**。

- 如果此操作成功，但当前为 S_OK **WeakRef**对象不派生自参数*U*。参数*ptr*设置为**nullptr**。

## <a name="remarks"></a>备注

如果发出错误参数*U*是`IWeakReference`，或不派生自`IInspectable`。

第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

从 Windows 10 SDK 开始，此方法不设置**WeakRef**实例向**nullptr**如果无法获得弱引用，因此应避免检查的 WeakRef 的错误检查代码**nullptr**。 相反，应检查*ptr*有关**nullptr**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[WeakRef 类](../windows/weakref-class.md)