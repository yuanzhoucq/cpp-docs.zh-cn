---
title: is_destructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd23064123513281099fa14a690679fa046657fe
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106621"
---
# <a name="isdestructible-class"></a>is_destructible 类

测试该类型是否易损坏。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是易损坏类型，否则为 false。 易损坏类型是引用类型、对象类型以及那些在其中对于等于 `U` 的某些类型 `remove_all_extents_t<T>` 而言未计算操作数 `std::declval<U&>.~U()` 格式正确的类型。 其他类型，包括不完整类型**void**，和函数类型，不是易损坏类型。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
