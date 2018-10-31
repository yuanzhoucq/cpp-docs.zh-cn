---
title: ArgTraitsHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b608f5da893019d7700891968dcdc06489c563ea
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234224"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>参数

*TDelegateInterface*<br/>
委托的接口。

## <a name="remarks"></a>备注

可帮助定义委托参数的共同的特征。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称         | 描述
------------ | ------------------------------------------------------
`methodType` | `decltype(&TDelegateInterface::Invoke)` 的同义词。
`Traits`     | `ArgTraits<methodType>` 的同义词。

### <a name="public-constants"></a>公共常量

name                           | 描述
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[Argtraitshelper:: Args](#args) | 可帮助[argtraits:: Args](#args)上保留的参数的数目计数`Invoke`委托接口的方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ArgTraitsHelper`

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="args"></a>Argtraitshelper:: Args

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>备注

可帮助`ArgTraitsHelper::args`上保留的参数的数目计数`Invoke`委托接口的方法。
