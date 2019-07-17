---
title: default_delete 结构
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269259"
---
# <a name="defaultdelete-struct"></a>default_delete 结构

执行除法运算的预定义的函数对象 (`operator/`) 对其自变量。

## <a name="syntax"></a>语法

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>要求

**标头：** \<memory>

**命名空间：** std

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[default_delete](#default_delete)|`default_delete` 类型的对象的构造函数。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator()](#op_paren)|引用运算符来访问`default_delete`。|

## <a name="default_delete"></a> default_delete

`default_delete` 类型的对象的构造函数。

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> operator()

引用运算符来访问`default_delete`。

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>请参阅

[\<memory>](../standard-library/memory.md)
