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
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360770"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>参数

*T委托接口*<br/>
委托接口。

## <a name="remarks"></a>备注

帮助定义委托参数的常见特征。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称         | 说明
------------ | ------------------------------------------------------
`methodType` | `decltype(&TDelegateInterface::Invoke)` 的同义词。
`Traits`     | `ArgTraits<methodType>` 的同义词。

### <a name="public-constants"></a>公共常量

名称                           | 说明
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[阿格·格萨尔特帮助者：：阿格斯](#args) | 帮助[ArgTraits：：args](#args)在委托接口`Invoke`的方法上保留参数数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ArgTraitsHelper`

## <a name="requirements"></a>要求

**标题：** 事件.h

**命名空间：** 微软：：WRL：:D

## <a name="argtraitshelperargs"></a><a name="args"></a>阿格·格萨尔特帮助者：：阿格斯

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>备注

帮助`ArgTraitsHelper::args`保留委托接口方法上的`Invoke`参数数。
