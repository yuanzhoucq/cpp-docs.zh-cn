---
title: FactoryCache 结构
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371490"
---
# <a name="factorycache-structure"></a>FactoryCache 结构

支持 Windows 运行时C++模板库基础结构，并且不打算直接从代码中使用。

## <a name="syntax"></a>语法

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>备注

包含类工厂的位置和标识已注册的 wrt 或 COM 类对象的值。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

名称                              | 说明
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[工厂缓存：：饼干](#cookie)   | 包含标识已注册的 Windows 运行时或 COM 类对象的值，以后用于取消注册该对象。
[工厂缓存：：工厂](#factory) | 指向 Windows 运行时或 COM 类工厂。

## <a name="inheritance-hierarchy"></a>继承层次结构

`FactoryCache`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** 微软：：WRL：:D

## <a name="factorycachecookie"></a><a name="cookie"></a>工厂缓存：：饼干

支持 Windows 运行时C++模板库基础结构，并且不打算直接从代码中使用。

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>备注

包含标识已注册的 Windows 运行时或 COM 类对象的值，以后用于取消注册该对象。

## <a name="factorycachefactory"></a><a name="factory"></a>工厂缓存：：工厂

支持 Windows 运行时C++模板库基础结构，并且不打算直接从代码中使用。

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>备注

指向 Windows 运行时或 COM 类工厂。
