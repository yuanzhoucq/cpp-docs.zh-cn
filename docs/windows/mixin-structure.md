---
title: MixIn 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: e6c4fb2abd6c27f8feec4357e17ef71b385cb7a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464923"
---
# <a name="mixin-structure"></a>MixIn 结构

确保运行时类先后派生自 Windows 运行时接口（如果有）和经典 COM 接口。

## <a name="syntax"></a>语法

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>参数

*派生*<br/>
一个类型派生自[实现](../windows/implements-structure.md)结构。

*MixInType*<br/>
基类型。

*hasImplements*<br/>
**true**如果*MixInType*是派生自当前实现基类型;**false**否则为。

## <a name="remarks"></a>备注

如果从 Windows 运行时和 COM 接口派生的类，类声明列表必须先列出任何 Windows 运行时接口，然后任何经典 COM 接口。 **MixIn**可确保按正确的顺序指定接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`MixIn`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)