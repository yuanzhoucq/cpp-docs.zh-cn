---
title: InterfaceListHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 03bfed00147daef22fe91e6f061ea6720834090f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025106"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>参数

*T0*<br/>
模板参数 0，这是必需的。

*T1*<br/>
模板参数 1，即默认情况下未指定。

*T2*<br/>
模板参数 2，即默认情况下未指定。第三个模板参数。

*T3*<br/>
模板参数 3，即默认情况下未指定。

*T4*<br/>
模板参数 4，即默认情况下未指定。

*T5*<br/>
模板参数 5，即默认情况下未指定。

*T6*<br/>
模板参数，6，即默认情况下未指定。

*T7*<br/>
模板参数，7，即默认情况下未指定。

*T8*<br/>
模板参数，8，即默认情况下未指定。

*T9*<br/>
模板参数，9，即默认情况下未指定。

## <a name="remarks"></a>备注

生成`InterfaceList`通过以递归方式应用指定的模板参数自变量的类型。

**InterfaceListHelper**模板使用模板参数*T0*定义中的第一个数据成员`InterfaceList`结构，然后以递归方式应用**InterfaceListHelper**任何剩余的模板参数的模板。 **InterfaceListHelper**没有剩余的模板参数时，会停止。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`TypeT`|InterfaceList 类型的同义词。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceListHelper`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)