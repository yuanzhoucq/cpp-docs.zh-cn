---
title: MixIn 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: cfa03706bc6030b337009f7228466a26e242aa6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221531"
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
从[实现](implements-structure.md)结构派生的类型。

*MixInType*<br/>
基类型。

*hasImplements*<br/>
**`true`** 如果*MixInType*派生自当前实现的基类型，则为;**`false`** 否则为。

## <a name="remarks"></a>备注

如果类派生自 Windows 运行时和类 COM 接口，则类声明列表必须首先列出任何 Windows 运行时接口，然后列出任何经典 COM 接口。 **MixIn**确保按正确的顺序指定接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`MixIn`

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft：： WRL 命名空间](microsoft-wrl-namespace.md)
