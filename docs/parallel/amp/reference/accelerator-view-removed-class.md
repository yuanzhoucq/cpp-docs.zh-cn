---
title: accelerator_view_removed 类
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127119"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed 类

基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。

## <a name="syntax"></a>语法

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[accelerator_view_removed 构造函数](#ctor)|初始化 `accelerator_view_removed` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|返回一个 HRESULT 错误代码，指示移除 `accelerator_view` 对象的原因。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>要求

**标头：** amprt

**命名空间：** 并发

## <a name="ctor"></a>accelerator_view_removed

初始化[accelerator_view_removed](accelerator-view-removed-class.md)类的新实例。

### <a name="syntax"></a>语法

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>参数

*message*<br/>
错误说明。

*view_removed_reason*<br/>
指示 `accelerator_view` 对象移除原因的 HRESULT 错误代码。

### <a name="return-value"></a>返回值

`accelerator_view_removed` 类的新实例。

## <a name="get_view_removed_reason"></a>get_view_removed_reason

返回一个 HRESULT 错误代码，指示移除 `accelerator_view` 对象的原因。

### <a name="syntax"></a>语法

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
