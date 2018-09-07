---
title: is_nothrow_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36d078c567f3ca74fb3552cbe728076445dd6690
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110079"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable 类

测试的值是否*从*类型可以分配给*到*类型，以及赋值是否确定不引发。

## <a name="syntax"></a>语法

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>参数

*若要*<br/>
接收赋值的对象的类型。

*From*<br/>
提供值的对象的类型。

## <a name="remarks"></a>备注

表达式 `declval<To>() = declval<From>()` 必须格式正确，编译器必须已知此表达式不会引发。 这两*从*并*到*必须是完整类型**void**，或具有未知边界的数组。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
