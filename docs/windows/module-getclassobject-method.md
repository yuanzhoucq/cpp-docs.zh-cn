---
title: 'Module:: getclassobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e0c8996823de35bbfd85d595556db933f34238a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599217"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject 方法

检索类工厂的缓存。

## <a name="syntax"></a>语法

```cpp
 HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>参数

*clsid*  
类 ID。

*riid*  
您请求的接口 ID。

*ppv*  
指向返回对象的指针。

*服务器名称*  
中指定的服务器名称`ActivatableClassWithFactory`， `ActivatableClassWithFactoryEx`，或`ActivatableClass`宏; 或者**nullptr**若要获取默认服务器名称。

## <a name="return-value"></a>返回值

## <a name="remarks"></a>备注

仅对 COM 而不是 Windows 运行时使用此方法。 此方法仅公开`IClassFactory`方法。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
[Module 类](../windows/module-class.md)