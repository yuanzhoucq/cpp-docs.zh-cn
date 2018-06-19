---
title: is_trivially_copy_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c36808d375dd774286c3663a02fdc308cc4b2790
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857501"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable 类

测试类型是否具有普通复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>参数

`T` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `T` 是具有普通复制赋值运算符的类，则类型谓词的实例为 true；否则为 false。

如果类 `T` 的赋值构造函数为隐式提供，则为普通类，类 `T` 不具有虚拟函数，类 `T` 不具有虚拟基，类类型的所有非静态数据成员的类都具有普通赋值运算符，且类的类型数组的所有非静态数据成员的类具有普通赋值运算符。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
