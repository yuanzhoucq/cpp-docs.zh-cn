---
title: is_default_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 267f0d83ee8f92eb73bddfbcd383f59db83c8a83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850341"
---
# <a name="isdefaultconstructible-class"></a>is_default_constructible 类

测试类型是否具有默认构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>参数

`T` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `T` 是具有默认构造函数的类类型，则类型谓词的实例为 true，否则为 false。 这等效于谓词 `is_constructible<T>`。 类型 `T` 必须是一个完整类型、 `void`或未知绑定的数组。

## <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}

```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
