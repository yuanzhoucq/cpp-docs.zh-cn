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
ms.openlocfilehash: b43d5bb2f553d298584ab2ae497c22637d3beb0d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58783847"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper 类

初始化 Windows 运行时。

## <a name="syntax"></a>语法

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>备注

`RoInitializeWrapper` 为方便起见，初始化 Windows 运行时并返回一个 HRESULT，指示操作是否成功。 因为类析构函数调用`::Windows::Foundation::Uninitialize`，实例的`RoInitializeWrapper`必须在全局或顶级范围内声明。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                                    | 描述
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | 初始化 `RoInitializeWrapper` 类的新实例。
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | 销毁的当前实例`RoInitializeWrapper`类。

### <a name="public-operators"></a>公共运算符

名称                                       | 描述
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | 检索生成的 HRESULT`RoInitializeWrapper`构造函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`RoInitializeWrapper`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers

## <a name="hresult"></a>RoInitializeWrapper::HRESULT()

检索最后一个生成的 HRESULT 值`RoInitializeWrapper`构造函数。

```cpp
operator HRESULT()
```

## <a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

初始化 `RoInitializeWrapper` 类的新实例。

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>参数

*flags*<br/>
RO_INIT_TYPE 枚举，指定 Windows 运行时提供的支持之一。

### <a name="remarks"></a>备注

`RoInitializeWrapper`类调用`Windows::Foundation::Initialize(flags)`。

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::~RoInitializeWrapper

取消初始化 Windows 运行时。

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>备注

`RoInitializeWrapper`类调用`Windows::Foundation::Uninitialize()`。
