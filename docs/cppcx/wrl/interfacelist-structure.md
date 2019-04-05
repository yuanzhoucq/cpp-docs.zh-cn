---
title: InterfaceList 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 745348e81888b5a87c57fbb99d397fcd423c3ee1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025544"
---
# <a name="interfacelist-structure"></a>InterfaceList 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>参数

*T*<br/>
接口名称;递归列表中的第一个接口。

*U*<br/>
接口名称;其余的接口中的递归列表。

## <a name="remarks"></a>备注

用于创建接口的递归列表。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`FirstT`|模板参数的同义词*T*。|
|`RestT`|模板参数的同义词*U*。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceList`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](microsoft-wrl-details-namespace.md)