---
title: '&lt;type_traits&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: 3754af9a32ab1beeb4f3b9a783547bd081d57a46
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955822"
---
# <a name="lttypetraitsgt-functions"></a>&lt;type_traits&gt; 函数

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable](#is_trivially_move_assignable)|
|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>is_assignable

测试的值是否*从*类型可以分配给*到*类型。

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>参数

*若要*  
 接收赋值的对象的类型。

*From*  
 提供值的对象的类型。

### <a name="remarks"></a>备注

未计算的表达式 `declval<To>() = declval<From>()` 必须具有正确格式。 这两*从*并*到*必须是完整类型**void**，或具有未知边界的数组。

## <a name="is_copy_assignable"></a>  is_copy_assignable

测试是否可以在赋值时复制类型。

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>参数

*Ty*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是具有复制赋值运算符，否则为 false 的类。 等效于 is_assignable\<Ty&, const Ty&>。

## <a name="is_copy_constructible"></a>  is_copy_constructible

测试类型是否包含复制构造函数。

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>参数

*Ty*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是具有复制构造函数，否则为 false 的类。

### <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}

```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a>  is_default_constructible

测试类型是否具有默认构造函数。

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>参数

*T*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是具有默认构造函数，否则为 false 的类类型。 这等效于谓词 `is_constructible<T>`。 类型*T*必须是完整类型**void**，或未知边界的数组。

### <a name="example"></a>示例

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

## <a name="is_move_assignable"></a>  is_move_assignable

测试类型是否可移动赋值。

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>参数

*T*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型的右值引用可赋予此类型的引用，则该类型可移动赋值。 类型谓词等效于 `is_assignable<T&, T&&>`。 可移动赋值的类型包括可引用的标量类型和类类型，这些类型具有编译器生成的移动赋值运算符或用户定义的移动赋值运算符。

## <a name="is_move_constructible"></a>  is_move_constructible

测试类型是否具有移动构造函数。

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>参数

*T*  
 要计算的类型

### <a name="remarks"></a>备注

类型谓词的计算结果为 true 的类型*T*可以通过使用移动操作构造。 此谓词等效于 `is_constructible<T, T&&>`。

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable

测试类型是否具有 **nothrow** 移动赋值运算符。

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>参数

*Ty*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*具有 nothrow 移动赋值运算符，否则为 false。

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable

测试类型是否具有普通复制赋值运算符。

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>参数

*T*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是具有普通复制赋值运算符，否则为 false 的类。

一个类的赋值构造函数*T*并不重要，如果它隐式提供，该类*T*没有虚函数，类*T*没有虚拟基，类类类型的所有非静态数据成员具有普通赋值运算符和类的类型数组的所有非静态数据成员的类具有普通赋值运算符。

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable

测试类型是否具有普通移动赋值运算符。

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>参数

*Ty*  
 要查询的类型。

### <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是具有普通移动赋值运算符，否则为 false 的类。

移动赋值运算符的类*Ty*并不重要如果：

它被隐式提供

该类*Ty*不具有虚拟函数

该类*Ty*不具有虚拟基

类类型的所有非静态数据成员的类具有普通移动赋值运算符

类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible

测试类型是否具有普通移动构造函数。

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>参数

*Ty*  
 要查询的类型。

### <a name="remarks"></a>备注

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

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
