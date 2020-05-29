---
title: InterfaceList 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213858"
---
# <a name="interfacelist-structure"></a>InterfaceList 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>parameters

*T*<br/>
接口名称;递归列表中的第一个接口。

*U*<br/>
接口名称;递归列表中的其余接口。

## <a name="remarks"></a>备注

用于创建接口的递归列表。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`FirstT`|模板参数*T*的同义词。|
|`RestT`|模板参数*U*的同义词。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceList`

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)
