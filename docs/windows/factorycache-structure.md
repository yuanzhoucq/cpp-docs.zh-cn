---
title: FactoryCache 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d56779b5df33f75c9147d34b55f8c2fc65204a82
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234536"
---
# <a name="factorycache-structure"></a>FactoryCache 结构

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>备注

包含一个类工厂和值，该值标识已注册 wrt 或 COM 类对象的位置。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

名称                              | 描述
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[Factorycache:: Cookie](#cookie)   | 包含一个值，用于标识已注册的 Windows 运行时或 COM 类对象，并随后用于取消注册该对象。
[Factorycache:: Factory](#factory) | 指向 Windows 运行时或 COM 类工厂。

## <a name="inheritance-hierarchy"></a>继承层次结构

`FactoryCache`

## <a name="requirements"></a>要求

**标头：** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="cookie"></a>Factorycache:: Cookie

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>备注

包含一个值，用于标识已注册的 Windows 运行时或 COM 类对象，并随后用于取消注册该对象。

## <a name="factory"></a>Factorycache:: Factory

支持 Windows 运行时 c + + 模板库基础结构，不应在代码中直接使用。

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>备注

指向 Windows 运行时或 COM 类工厂。
