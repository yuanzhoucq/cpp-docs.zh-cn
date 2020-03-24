---
title: RemoveIUnknown 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213611"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>parameters

*T*<br/>
一个类。

## <a name="remarks"></a>备注

使类型等效于基于 `IUnknown`的类型，但具有非虚拟 `QueryInterface`、`AddRef`和 `Release` 成员函数。

默认情况下，COM 方法提供虚拟 `QueryInterface`、`AddRef`和 `Release` 方法。 但 `ComPtr` 不需要虚拟方法的系统开销。 `RemoveIUnknown` 通过提供私有、非虚拟 `QueryInterface`、`AddRef`和 `Release` 方法来消除这种开销。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`ReturnType`|与模板参数*T*等效但具有非虚拟 `IUnknown` 成员的类型的同义词。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`RemoveIUnknown`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)
