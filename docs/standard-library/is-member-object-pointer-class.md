---
title: is_member_object_pointer 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_member_object_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_member_object_pointer class
- is_member_object_pointer
ms.assetid: 64f9cdf3-4621-4310-a076-a7bc986926b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a045abd8bb6a41e96febf972d21bae80b9b4f7a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955411"
---
# <a name="ismemberobjectpointer-class"></a>is_member_object_pointer 类

测试类型是否为指向成员对象的指针。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_member_object_pointer;
```

### <a name="parameters"></a>参数

*Ty*查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是指向成员对象的指针或`cv-qualified`指向成员对象; 否则为 false。 请注意，`is_member_object_pointer`持有 false if *Ty*是指向成员函数的指针。

## <a name="example"></a>示例

```cpp
// std__type_traits__is_member_object_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_object_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_object_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_object_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_object_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_object_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }

```

```Output
is_member_object_pointer<trivial *> == false
is_member_object_pointer<int trivial::*> == true
is_member_object_pointer<int (functional::*)()> == false
```

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer 类](../standard-library/is-member-pointer-class.md)<br/>
