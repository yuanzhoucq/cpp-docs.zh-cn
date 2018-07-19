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
ms.openlocfilehash: 9f7c4c748d7328f534aebfb2133c72635bbdc36f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953961"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable 类

测试类型是否具有普通复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>参数

*T*查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是具有普通复制赋值运算符，否则为 false 的类。

一个类的赋值构造函数*T*并不重要，如果它隐式提供，该类*T*没有虚函数，类*T*没有虚拟基，类类类型的所有非静态数据成员具有普通赋值运算符和类的类型数组的所有非静态数据成员的类具有普通赋值运算符。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
