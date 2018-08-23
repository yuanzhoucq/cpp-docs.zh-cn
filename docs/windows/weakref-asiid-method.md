---
title: 'Weakref:: Asiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8844828028e174bd216bddb7e7c82cc9e5971a90
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594878"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID 方法

设置指定`ComPtr`指针参数以表示指定的接口 id。

## <a name="syntax"></a>语法

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>参数

*riid*  
接口 ID。

*ptr*  
此操作完成后，一个对象，表示参数*riid*。

## <a name="return-value"></a>返回值

- 如果此操作成功，则为 S_OK否则，一个 HRESULT，指示的原因，操作失败，并*ptr*设置为**nullptr**。

- 如果此操作成功，但当前为 S_OK **WeakRef**已释放对象。 参数*ptr*设置为**nullptr**。

- 如果此操作成功，但当前为 S_OK **WeakRef**对象不派生自参数*riid*。 参数*ptr*设置为**nullptr**。 (有关更多信息，请参阅“备注”。)

## <a name="remarks"></a>备注

如果发出错误参数*riid*不派生自`IInspectable`。 此错误将取代返回值。

第一个模板是应在代码中使用的表单。 第二个模板（此处未显示，但在头文件中声明）是支持 [自动](../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。

从 Windows 10 SDK 开始，此方法不设置**WeakRef**实例向**nullptr**如果无法获得弱引用，因此应避免的错误检查代码，用于检查**WeakRef**有关**nullptr**。 相反，应检查*ptr*有关**nullptr**。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[WeakRef 类](../windows/weakref-class.md)