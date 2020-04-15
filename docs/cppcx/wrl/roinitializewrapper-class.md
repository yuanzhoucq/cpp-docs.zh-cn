---
title: RoInitializeWrapper 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371222"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 类

初始化 Windows 运行时。

## <a name="syntax"></a>语法

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>备注

`RoInitializeWrapper`是初始化 Windows 运行时并返回指示操作是否成功的 HRESULT 的便利。 由于类析构函数调用`::Windows::Foundation::Uninitialize`，必须在全局`RoInitializeWrapper`或顶级作用域中声明 的 实例。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                    | 说明
----------------------------------------------------------------------- | -----------------------------------------------------------------
[放大缩小字体功能 放大缩小字体功能](#roinitializewrapper)        | 初始化 `RoInitializeWrapper` 类的新实例。
[Ro初始化包装器：：\Ro初始化包装器](#tilde-roinitializewrapper) | 销毁`RoInitializeWrapper`类的当前实例。

### <a name="public-operators"></a>公共运算符

名称                                       | 说明
------------------------------------------ | ------------------------------------------------------------------------
[放大缩小字体功能 放大缩小字体功能](#hresult) | 检索`RoInitializeWrapper`构造函数生成的 HRESULT。

## <a name="inheritance-hierarchy"></a>继承层次结构

`RoInitializeWrapper`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>放大缩小字体功能 放大缩小字体功能

检索最后`RoInitializeWrapper`一个构造函数生成的 HRESULT 值。

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>放大缩小字体功能 放大缩小字体功能

初始化 `RoInitializeWrapper` 类的新实例。

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>参数

*标志*<br/>
RO_INIT_TYPE枚举之一，它指定 Windows 运行时提供的支持。

### <a name="remarks"></a>备注

类`RoInitializeWrapper`调用`Windows::Foundation::Initialize(flags)`。

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>Ro初始化包装器：：\Ro初始化包装器

取消初始化 Windows 运行时。

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>备注

类`RoInitializeWrapper`调用`Windows::Foundation::Uninitialize()`。
