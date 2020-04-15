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
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371355"
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

*基地*<br/>
基类型。

*派生*<br/>
派生类型。

## <a name="remarks"></a>备注

测试一种类型是否是另一种类型的基类。

第一个模板测试类型是否派生自基类型，该基类型可能产生**真**或**假**。 第二个模板测试类型是否派生自自身，后者始终生成**false**。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

名称                            | 说明
------------------------------- | --------------------------------------------------
[是严格的基础：：值](#value) | 指示一种类型是否是另一种类型的基础。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsBaseOfStrict`

## <a name="requirements"></a>要求

**标题：** 内部.h

**命名空间：** 微软：：WRL：:D

## <a name="isbaseofstrictvalue"></a><a name="value"></a>是严格的基础：：值

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>备注

指示一种类型是否是另一种类型的基础。

`value`如果类型`Base`是类型的`Derived`基类，则为**true，** 否则为**false**。
