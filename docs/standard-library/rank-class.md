---
title: rank 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::rank
dev_langs:
- C++
helpviewer_keywords:
- rank class
- rank
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be250d2908522ac85902563d64bf57ca7cde88a0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="rank-class"></a>rank 类

获取数组维度数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct rank;
```

### <a name="parameters"></a>参数

`Ty` 查询的类型。

## <a name="remarks"></a>备注

类型查询会保留数组类型 `Ty` 的维度数值，如果 `Ty` 不是数组类型，则为 0。

## <a name="example"></a>示例

```cpp
// std__type_traits__rank.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "rank<int> == "
        << std::rank<int>::value << std::endl;
    std::cout << "rank<int[5]> == "
        << std::rank<int[5]>::value << std::endl;
    std::cout << "rank<int[5][10]> == "
        << std::rank<int[5][10]>::value << std::endl;

    return (0);
    }

```

```Output
rank<int> == 0
rank<int[5]> == 1
rank<int[5][10]> == 2
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[extent 类](../standard-library/extent-class.md)<br/>
