---
title: IsSame 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371345"
---
# <a name="issame-structure"></a>IsSame 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>参数

*T1*<br/>
一种类型。

*T2*<br/>
另一种类型。

## <a name="remarks"></a>备注

测试一个指定类型是否与另一个指定类型相同。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

名称                    | 说明
----------------------- | --------------------------------------------------
[相同：值](#value) | 指示一种类型是否与另一种类型相同。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsSame`

## <a name="requirements"></a>要求

**标题：** 内部.h

**命名空间：** 微软：：WRL：:D

## <a name="issamevalue"></a><a name="value"></a>相同：值

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>备注

指示一种类型是否与另一种类型相同。

`value`如果模板参数相同，**则为 true;** 如果模板参数不同，**则为 false。**
