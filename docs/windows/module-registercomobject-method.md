---
title: 'Module:: registercomobject 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7cccebf6e1c6004a2416f4fdeb254369f9aa7b72
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410307"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject 方法

注册一个或多个 COM 对象，以便其他应用程序可连接到它们。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);

```

### <a name="parameters"></a>参数

*服务器名称*<br/>
服务器的完全限定名。

*clsid*<br/>
要注册的 CLSID 的数组。

*工厂*<br/>
其可用性正发布的类对象的 IUnknown 接口的数组。

*Cookie*<br/>
完成此操作后，指向标识已注册类对象的值的指针数组。 以后将使用这些值来撤销注册。

*count*<br/>
要注册的 CLSID 的数量。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。

## <a name="remarks"></a>备注

COM 对象是使用 CLSCTX 枚举的 CLSCTX_LOCAL_SERVER 枚举器注册的。

当前的组合来指定连接到已注册的对象的类型*comflag*模板参数，并结合枚举的 REGCLS_SUSPENDED 枚举器。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)