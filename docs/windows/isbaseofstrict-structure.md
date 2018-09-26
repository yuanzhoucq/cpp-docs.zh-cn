---
title: IsBaseOfStrict 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 137f572f01d4aa72b9141c3ca172426fdb575b48
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169519"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>参数

*基本*<br/>
基类型。

*派生*<br/>
派生的类型。

## <a name="remarks"></a>备注

测试一种类型是否是另一种类型的基类。

第一个模板测试是否从可能产生的基类型派生的类型`true`或`false`。 第二个模板测试是否派生的类型是从其自身，这将始终产生`false`。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

name                            | 描述
------------------------------- | --------------------------------------------------
[Isbaseofstrict:: Value](#value) | 指示是否是一个类型的另一个基类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsBaseOfStrict`

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="value"></a>Isbaseofstrict:: Value

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>备注

指示是否是一个类型的另一个基类。

`value` 是`true`如果类型`Base`是类型的基类`Derived`，否则它是`false`。
