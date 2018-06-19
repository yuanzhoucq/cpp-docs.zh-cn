---
title: is_fundamental 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_fundamental
dev_langs:
- C++
helpviewer_keywords:
- is_fundamental class
- is_fundamental
ms.assetid: b84eee84-2fb2-4611-beaf-b384074d8b6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e210af223ffe6d3b8e0766adaaf539f0bb97f73
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844362"
---
# <a name="isfundamental-class"></a>is_fundamental 类

测试类型是 void 还是算术类型。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_fundamental;
```

### <a name="parameters"></a>参数

`Ty` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `Ty` 是基本类型（即 `void`、整数类型、浮点类型或前述其中一个类型的 `cv-qualified` 形式），则类型谓词的实例将为 true，否则为 false。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_fundamental.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_fundamental<trivial> == " << std::boolalpha
        << std::is_fundamental<trivial>::value << std::endl;
    std::cout << "is_fundamental<int> == " << std::boolalpha
        << std::is_fundamental<int>::value << std::endl;
    std::cout << "is_fundamental<const float> == " << std::boolalpha
        << std::is_fundamental<const float>::value << std::endl;
    std::cout << "is_fundamental<void> == " << std::boolalpha
        << std::is_fundamental<void>::value << std::endl;

    return (0);
    }

```

```Output
is_fundamental<trivial> == false
is_fundamental<int> == true
is_fundamental<const float> == true
is_fundamental<void> == true
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_compound 类](../standard-library/is-compound-class.md)<br/>
