---
title: IsBaseOfStrict 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 85aeb71ceaa162cc6366836dd286f2f9983d34e2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784111"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>参数

*基本*<br/>
基类型。

*派生*<br/>
派生的类型。

## <a name="remarks"></a>备注

测试一种类型是否是另一种类型的基类。

第一个模板测试是否从可能产生的基类型派生的类型 **，则返回 true**或**false**。 第二个模板测试是否派生的类型是从其自身，这将始终产生**false**。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

名称                            | 描述
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | 指示是否是一个类型的另一个基类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsBaseOfStrict`

## <a name="requirements"></a>要求

**标头：** internal.h

**命名空间：** Microsoft::WRL::Details

## <a name="value"></a>IsBaseOfStrict::value

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>备注

指示是否是一个类型的另一个基类。

`value` 是 **，则返回 true**如果类型`Base`是类型的基类`Derived`，否则是**false**。
