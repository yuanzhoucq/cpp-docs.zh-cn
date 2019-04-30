---
title: ArgTraitsHelper 结构
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398831"
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

名称                           | 描述
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | 可帮助[argtraits:: Args](#args)上保留的参数的数目计数`Invoke`委托接口的方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ArgTraitsHelper`

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL::Details

## <a name="args"></a>ArgTraitsHelper::args

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>备注

可帮助`ArgTraitsHelper::args`上保留的参数的数目计数`Invoke`委托接口的方法。
