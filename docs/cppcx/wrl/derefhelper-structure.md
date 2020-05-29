---
title: DerefHelper 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 43453d3162de697fa1cfcf0581953c91bbe3934f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214040"
---
# <a name="derefhelper-structure"></a>DerefHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>parameters

*T*<br/>
模板参数。

## <a name="remarks"></a>备注

表示指向 `T*` 模板参数的取消引用的指针。

**DerefHelper**用于如下所示的表达式： `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`DerefType`|取消引用的模板参数 `T*`的标识符。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`DerefHelper`

## <a name="requirements"></a>要求

**标头：** async。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)
