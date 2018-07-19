---
title: is_trivially_move_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316ffdee4905ff8a35baef7137ff7f28a2846786
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958187"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible 类

测试类型是否具有普通移动构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>参数

*Ty*查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是一个类具有普通移动构造函数，否则为 false。

移动构造函数的类*Ty*并不重要如果：

它被隐式声明

其参数类型等效于那些隐式声明的参数类型

该类*Ty*不具有虚拟函数

该类*Ty*不具有虚拟基

类没有任何不稳定的非静态数据成员

类的所有直接都基均*Ty*具有普通移动构造函数

类类型的所有非静态数据成员的类具有普通构造函数

类的类型数组的所有非静态数据成员的类具有普通构造函数

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
