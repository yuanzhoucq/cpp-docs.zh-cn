---
title: ArgTraitsHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb0377de88ef5e782e0e11bc563409b7094eecf5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598679"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>参数

*TDelegateInterface*  
委托的接口。

## <a name="remarks"></a>备注

可帮助定义委托参数的共同的特征。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`methodType`|`decltype(&TDelegateInterface::Invoke)` 的同义词。|
|`Traits`|`ArgTraits<methodType>` 的同义词。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[ArgTraitsHelper::args 常量](../windows/argtraitshelper-args-constant.md)|可帮助[argtraits:: Args](../windows/argtraits-args-constant.md)上保留的参数的数目计数`Invoke`委托接口的方法。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`ArgTraitsHelper`

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)