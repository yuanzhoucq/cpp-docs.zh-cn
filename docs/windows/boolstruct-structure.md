---
title: BoolStruct 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74a292f2253d29730e8ee9104ea81308081c0496
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234263"
---
# <a name="boolstruct-structure"></a>BoolStruct 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>备注

`BoolStruct`结构定义是否`ComPtr`管理接口的对象生存期。 `BoolStruct` 在内部使用[BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)运算符。

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

名称                          | 描述
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct:: Member](#member) | 指定的[ComPtr](../windows/comptr-class.md) ，或不管理接口的对象生存期。

## <a name="inheritance-hierarchy"></a>继承层次结构

`BoolStruct`

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="member"></a>Boolstruct:: Member

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
int Member;
```

### <a name="remarks"></a>备注

指定的[ComPtr](../windows/comptr-class.md) ，或不管理接口的对象生存期。
