---
title: 'Comptr:: Copyto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9b84cbcc970183222ed06752dc61b5672615868
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405380"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo 方法

将复制与此相关联的当前或指定界面**ComPtr**到指定的指针。

## <a name="syntax"></a>语法

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>参数

*U*<br/>
类型名称。

*ptr*<br/>
此操作完成后，指向所请求的接口的指针。

*riid*<br/>
接口 ID。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为一个 HRESULT，指示原因的隐式`QueryInterface`操作失败。

## <a name="remarks"></a>备注

在第一个函数返回与此相关联的接口的指针的副本**ComPtr**。 此函数始终返回 S_OK。

第二个函数执行`QueryInterface`与此相关联的接口上的操作**ComPtr**为指定的接口*riid*参数。

第三个函数执行`QueryInterface`与此相关联的接口上的操作**ComPtr**基础接口*U*参数。

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ComPtr 类](../windows/comptr-class.md)