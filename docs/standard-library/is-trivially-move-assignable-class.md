---
title: is_trivially_move_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae0db2b789e16a39396a329a64dfb8794eef5775
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961904"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 类

测试类型是否具有普通移动赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>参数

*Ty*查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是具有普通移动赋值运算符，否则为 false 的类。

移动赋值运算符的类*Ty*并不重要如果：

它被隐式提供

该类*Ty*不具有虚拟函数

该类*Ty*不具有虚拟基

类类型的所有非静态数据成员的类具有普通移动赋值运算符

类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
