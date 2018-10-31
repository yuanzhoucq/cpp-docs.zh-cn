---
title: IsSame 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af59860016835f8e8dfddc9d0a77204ff866bd3
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161848"
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

T1<br/>
一种类型。

T2<br/>
另一种类型。

## <a name="remarks"></a>备注

一个指定类型等同于另一个测试指定的类型。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

name                    | 描述
----------------------- | --------------------------------------------------
[Issame:: Value](#value) | 指示一种类型是否与另一个相同。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsSame`

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="value"></a>Issame:: Value

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

指示一种类型是否与另一个相同。

`value` 是 **，则返回 true**如果模板参数相同，并且**false**如果模板参数不同。
