---
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: 94178d2efd1942a7475fa7987526b021b1c6fb68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87201955"
---
# <a name="lttype_traitsgt"></a>&lt;type_traits&gt;

定义编译时常数的模板，这些常数提供有关其类型参数的属性的信息或生成转换类型。

## <a name="syntax"></a>语法

```cpp
#include <type_traits>
```

## <a name="remarks"></a>备注

中的类和模板 \<type_traits> 用于在编译时支持类型推理、分类和转换。 它们还用于检测与类型相关的错误，有助于优化一般代码。 一元类型特征描述类型的属性，二进制类型特征描述类型之间的关系，转换特征修改类型的属性。

Helper 类 `integral_constant` 及其模板专用化 `true_type` 并 `false_type` 形成类型谓词的基类。 类型谓词** 是采用一个或多个类型参数的模板。 当类型谓词*为 true*时，它是从[true_type](../standard-library/type-traits-typedefs.md#true_type)中直接或间接派生的。 当类型谓词*为 false*时，它将从[false_type](../standard-library/type-traits-typedefs.md#false_type)中直接或间接派生。

类型修饰符** 或转换特征** 是一个模板，包含一个或多个参数以及一个成员 `type`（即修改后的类型）。

### <a name="alias-templates"></a>别名模板

为了简化类型特征表达式，提供了的[别名模板](../cpp/aliases-and-typedefs-cpp.md) `typename some_trait<T>::type` ，其中*some_trait*为类模板名称。 例如，[add_const](../standard-library/add-const-class.md) 具有其类型 `add_const_t` 的别名模板，定义如下：

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

这些是为成员提供的别名 `type` ：

||||
|-|-|-|
| add_const_t | add_cv_t | add_lvalue_reference_t |
| add_pointer_t | add_rvalue_reference_t | add_volatile_t |
| aligned_storage_t | aligned_union_t | common_type_t |
| conditional_t | decay_t | enable_if_t |
| invoke_result_t | make_signed_t | make_unsigned_t |
| remove_all_extents_t | remove_const_t | remove_cv_t |
| remove_extent_t | remove_pointer_t | remove_reference_t |
| remove_volatile_t | result_of_t | underlying_type_t |

### <a name="classes"></a>类

帮助程序类和 typedef

|||
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|从类型和值生成整型常量。|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|保留包含值 true 的整数常量。|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|保留包含值 false 的整数常量。|

主要类型类别

|||
|-|-|
|[is_void](../standard-library/is-void-class.md)|测试类型是否为 **`void`** 。|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|测试类型是否为 `std::nullptr_t`。|
|[is_integral](../standard-library/is-integral-class.md)|测试类型是否为整型。|
|[is_floating_point](../standard-library/is-floating-point-class.md)|测试类型是否为浮点。|
|[is_array](../standard-library/is-array-class.md)|测试类型是否为数组。|
|[is_pointer](../standard-library/is-pointer-class.md)|测试类型是否为指针。|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|测试类型是否是左值引用。|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|测试类型是否是右值引用。|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|测试类型是否为指向成员对象的指针。|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|测试类型是否为指向成员函数的指针。|
|[is_enum](../standard-library/is-enum-class.md)|测试类型是否为枚举。|
|[is_union](../standard-library/is-union-class.md)|测试类型是否为联合。|
|[is_class](../standard-library/is-class-class.md)|测试类型是否为类。|
|[is_function](../standard-library/is-function-class.md)|测试类型是否为函数类型。|

复合类型类别

|||
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|测试类型是否为引用。|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|测试类型是否为算术型。|
|[is_fundamental](../standard-library/is-fundamental-class.md)|测试类型是否为 **`void`** 或算术类型。|
|[is_object](../standard-library/is-object-class.md)|测试类型是否为对象类型。|
|[is_scalar](../standard-library/is-scalar-class.md)|测试类型是否为标量类型。|
|[is_compound](../standard-library/is-compound-class.md)|测试类型是否为非标量类型。|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|测试类型是否为指向成员的指针。|

Type 属性

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|测试类型是否为 **`const`** 。|
|[is_volatile](../standard-library/is-volatile-class.md)|测试类型是否为 **`volatile`** 。|
|[is_trivial](../standard-library/is-trivial-class.md)|测试类型是否常用。|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|测试类型是否可完全复制。|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|测试类型是否为标准布局类型。|
|[is_pod](../standard-library/is-pod-class.md)|测试类型是否为 POD。|
|[is_literal_type](../standard-library/is-literal-type-class.md)|测试类型是否可以是 **`constexpr`** 变量或在函数中使用 **`constexpr`** 。|
|[is_empty](../standard-library/is-empty-class.md)|测试类型是否为空类。|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|测试类型是否为多态类。|
|[is_abstract](../standard-library/is-abstract-class.md)|测试类型是否为抽象类。|
|[is_final](../standard-library/is-final-class.md)|测试类型是否是标记为 `final` 的类类型。|
|[is_aggregate](../standard-library/is-aggregate-class.md)||
|[is_signed](../standard-library/is-signed-class.md)|测试类型是否为有符号的整数。|
|[is_unsigned](../standard-library/is-unsigned-class.md)|测试类型是否为无符号的整数。|
|[is_constructible](../standard-library/is-constructible-class.md)|测试类型是否可使用指定参数类型进行构造。|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|测试类型是否包含默认构造函数。|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|测试类型是否包含复制构造函数。|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|测试类型是否具有移动构造函数。|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|测试是否可以将第二个类型的值分配给第一个类型。|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|测试是否可以将类型的常量引用值分配给该类型。|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|测试是否可以将类型的右值引用分配给该类型。|
|[is_swappable](../standard-library/type-traits-functions.md#is_swappable)||
|[is_swappable_with](../standard-library/type-traits-functions.md#is_swappable_with)||
|[is_destructible](../standard-library/is-destructible-class.md)|测试该类型是否易损坏。|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|测试在使用指定类型构造类型时，该类型是否未使用非常用操作。|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|测试在构造默认时，该类型是否未使用非常用操作。|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|测试在构造复制时，该类型是否未使用非常用操作。|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|测试在构造移动时，该类型是否未使用非常用操作。|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|测试类型是否可赋值，以及赋值是否未使用非常用操作。|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|测试类型是否为复制赋值，以及赋值是否未使用非常用操作。|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|测试类型是否为移动赋值，以及赋值是否未使用非常用操作。|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|测试类型是否易损坏，以及析构函数是否未使用非常用操作。|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|测试类型是否可构造，以及是否确定在使用指定类型进行构造时不引发。|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|测试类型是否是默认构造，以及是否确定在构造默认时不引发。|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|测试类型是否是复制构造，以及复制构造函数是否确定不引发。|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|测试类型是否是移动构造，以及移动构造函数是否确定不引发。|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|测试类型是否可使用指定类型进行赋值，以及赋值是否确定不引发。|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|测试类型是否是复制赋值，以及赋值是否确定不引发。|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|测试类型是否是移动赋值，以及赋值是否确定不引发。|
|[is_nothrow_swappable](../standard-library/type-traits-functions.md#is_nothrow_swappable)||
|[is_nothrow_swappable_with](../standard-library/type-traits-functions.md#is_nothrow_swappable_with)||
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|测试类型是否易损坏，以及析构函数是否确定不引发。|
|`has_virtual_destructor`|测试类型是否包含虚拟的析构函数。|
|`has_unique_object_representations`||
| [is_invocable](is-invocable-classes.md) | 测试是否可以使用指定的参数类型调用可调用类型。<br/> 在 c + + 17 中添加。 |
| [is_invocable_r](is-invocable-classes.md) | 测试可调用类型是否可使用指定的自变量类型调用，以及结果是否可转换为指定类型。<br/> 在 c + + 17 中添加。 |
| [is_nothrow_invocable](is-invocable-classes.md) | 测试可调用类型是否可使用指定的自变量类型调用，并且是否被认为不会引发异常。<br/> 在 c + + 17 中添加。 |
| [is_nothrow_invocable_r](is-invocable-classes.md) | 测试可调用类型是否可使用指定的自变量类型调用，以及是否已知不会引发异常，并且结果可转换为指定的类型。<br/> 在 c + + 17 中添加。 |

Type 属性查询

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|获取类型的对齐方式。|
|[级别](../standard-library/rank-class.md)|获取数组维度数。|
|[范围](../standard-library/extent-class.md)|获取指定数组维度中的元素数。|

类型关系

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|确定两个类型是否相同。|
|[is_base_of](../standard-library/is-base-of-class.md)|测试一种类型是否是另一种类型的基类。|
|[is_convertible](../standard-library/is-convertible-class.md)|测试一种类型是否可转换为另一种类型。|

Const-volatile 修改

|||
|-|-|
|[add_const](../standard-library/add-const-class.md)|**`const`** 从类型生成类型。|
|[add_volatile](../standard-library/add-volatile-class.md)|**`volatile`** 从类型生成类型。|
|[add_cv](../standard-library/add-cv-class.md)|**`const volatile`** 从类型生成类型。|
|[remove_const](../standard-library/remove-const-class.md)|从类型生成一个非常量类型。|
|[remove_volatile](../standard-library/remove-volatile-class.md)|从类型生成一个非易失类型。|
|[remove_cv](../standard-library/remove-cv-class.md)|从类型生成一个非常量非易失类型。|

引用修改

|||
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|从类型生成一个对类型的引用。|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|从类型生成一个对类型的右值引用|
|[remove_reference](../standard-library/remove-reference-class.md)|从类型生成一个非引用类型。|

签名修改

|||
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|如果有符号，则生成该类型，或大小大于或等于类型的最小有符号类型。|
|[make_unsigned](../standard-library/make-unsigned-class.md)|如果无符号，则生成该类型，或大小大于或等于类型的最小无符号类型。|

数组修改

|||
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|从数组类型生成一个非数组类型。|
|[remove_extent](../standard-library/remove-extent-class.md)|从数组类型生成一个元素类型。|

指针修改

|||
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|从类型生成指向类型的指针。|
|[remove_pointer](../standard-library/remove-pointer-class.md)|从指向类型的指针生成一个类型。|

其他转换

|||
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|为对齐类型分配未初始化的内存。|
|[aligned_union](../standard-library/aligned-union-class.md)|为具有不常用构造函数或析构函数的对齐联合分配未初始化的内存。|
|[common_type](../standard-library/common-type-class.md)|生成参数包的所有类型的通用类型。|
|[增值税](../standard-library/conditional-class.md)|如果条件为 true，则生成第一个指定类型，否则生成第二个指定类型。|
|[decay](../standard-library/decay-class.md)|生成按值传递的类型。 设置非引用、非常量或非可变类型或者设置指向类型的指针。|
|[enable_if](../standard-library/enable-if-class.md)|如果条件为 true，则生成指定类型，否则不生成类型。|
|[invoke_result](invoke-result-class.md)|确定可调用类型的返回类型，该可调用类型采用指定参数类型。 <br/>在 c + + 17 中添加。 |
|[result_of](../standard-library/result-of-class.md)|确定可调用类型的返回类型，该可调用类型采用指定参数类型。 <br/>在 c + + 14 中添加，在 c + + 17 中已弃用。 |
|[underlying_type](../standard-library/underlying-type-class.md)|生成枚举类型的基础整型类型。|

逻辑运算符特征

|||
|-|-|
|[连接](../standard-library/conjunction-class.md)||
|[析取](../standard-library/disjunction-class.md)||
|[求反](../standard-library/negation-class.md)||

## <a name="see-also"></a>另请参阅

[\<functional>](../standard-library/functional.md)
