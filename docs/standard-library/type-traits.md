---
title: '&lt;type_traits&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <type_traits>
dev_langs:
- C++
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed2cad9c96b20313617ef57e4373de16712aa34
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218847"
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;

定义了提供编译时常数的模板，这些常数可提供有关其类型参数的属性的信息或生成转换类型。

## <a name="syntax"></a>语法

```cpp
#include <type_traits>
```

## <a name="remarks"></a>备注

类和模板\<type_traits > 用于支持类型推理、 分类和转换在编译时，检测类型相关的错误，并帮助你优化泛型代码。 这些类和模板包括描述类型属性的一元类型特征、描述类型间关系的二元类型特征，以及修改类型属性的转换特征。

若要支持类型特征，需定义一个帮助程序类 `integral_constant`。 它具有可构成类型谓词的基类的模板专用化 `true_type` 和 `false_type`。 类型谓词是采用一个或多个类型参数的模板。 如果类型谓词保留为 true，则它是以公共方式直接或间接从 [true_type](../standard-library/type-traits-typedefs.md#true_type) 派生的。 如果类型谓词保留为 false，则它是以公共方式直接或间接从 [false_type](../standard-library/type-traits-typedefs.md#false_type) 派生的。

类型修饰符或转换特征是一个模板，包含一个或多个参数以及一个成员 `type`（即修改后的类型）。

### <a name="alias-templates"></a>别名模板

为了简化类型特征表达式，提供了 `typename some_trait<T>::type` 的[别名模板](../cpp/aliases-and-typedefs-cpp.md)，其中“`some_trait`”是模板类名称。 例如，[add_const](../standard-library/add-const-class.md) 具有其类型 `add_const_t` 的别名模板，定义如下：

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

|||||
|-|-|-|-|
|add_const_t|aligned_storage_t|make_signed_t|remove_pointer_t|
|add_cv_t|aligned_union_t|make_unsigned_t|remove_reference_t|
|add_lvalue_reference_t|common_type_t|remove_all_extents_t|remove_volatile_t|
|add_pointer_t|conditional_t|remove_const_t|result_of_t|
|add_rvalue_reference_t|decay_t|remove_cv_t|underlying_type_t|
|add_volatile_t|enable_if_t|remove_extent_t||

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
|[is_void](../standard-library/is-void-class.md)|测试类型是否为**void**。|
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
|[is_fundamental](../standard-library/is-fundamental-class.md)|测试类型是否为**void**或算术。|
|[is_object](../standard-library/is-object-class.md)|测试类型是否为对象类型。|
|[is_scalar](../standard-library/is-scalar-class.md)|测试类型是否为标量类型。|
|[is_compound](../standard-library/is-compound-class.md)|测试类型是否为非标量类型。|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|测试类型是否为指向成员的指针。|

类型属性

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|测试类型是否为**const**。|
|[is_volatile](../standard-library/is-volatile-class.md)|测试类型是否为**易失性**。|
|[is_trivial](../standard-library/is-trivial-class.md)|测试类型是否常用。|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|测试类型是否可完全复制。|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|测试类型是否为标准布局类型。|
|[is_pod](../standard-library/is-pod-class.md)|测试类型是否为 POD。|
|[is_literal_type](../standard-library/is-literal-type-class.md)|测试类型是否可以是 `constexpr` 变量或是否可用于 `constexpr` 函数。|
|[is_empty](../standard-library/is-empty-class.md)|测试类型是否为空类。|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|测试类型是否为多态类。|
|[is_abstract](../standard-library/is-abstract-class.md)|测试类型是否为抽象类。|
|[is_final](../standard-library/is-final-class.md)|测试类型是否是标记为 `final` 的类类型。|
|[is_signed](../standard-library/is-signed-class.md)|测试类型是否为有符号的整数。|
|[is_unsigned](../standard-library/is-unsigned-class.md)|测试类型是否为无符号的整数。|
|[is_constructible](../standard-library/is-constructible-class.md)|测试类型是否可使用指定参数类型进行构造。|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|测试类型是否包含默认构造函数。|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|测试类型是否包含复制构造函数。|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|测试类型是否具有移动构造函数。|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|测试是否可以将第二个类型的值分配给第一个类型。|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|测试是否可以将类型的常量引用值分配给该类型。|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|测试是否可以将类型的右值引用分配给该类型。|
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
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|测试类型是否易损坏，以及析构函数是否确定不引发。|
|[has_virtual_destructor](https://msdn.microsoft.com/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|测试类型是否包含虚拟的析构函数。|

Type 属性查询

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|获取类型的对齐方式。|
|[rank](../standard-library/rank-class.md)|获取数组维度数。|
|[extent](../standard-library/extent-class.md)|获取指定数组维度中的元素数。|

类型关系

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|确定两个类型是否相同。|
|[is_base_of](../standard-library/is-base-of-class.md)|测试一种类型是否是另一种类型的基类。|
|[is_convertible](../standard-library/is-convertible-class.md)|测试一种类型是否可转换为另一种类型。|

Const-volatile 修改

|||
|-|-|
|[add_const](../standard-library/add-const-class.md)|将生成**const**从类型的类型。|
|[add_volatile](../standard-library/add-volatile-class.md)|将生成**易失性**从类型的类型。|
|[add_cv](../standard-library/add-cv-class.md)|将生成**const 易失性**从类型的类型。|
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
|[conditional](../standard-library/conditional-class.md)|如果条件为 true，则生成第一个指定类型，否则生成第二个指定类型。|
|[decay](../standard-library/decay-class.md)|生成按值传递的类型。 设置非引用、非常量或非可变类型或者设置指向类型的指针。|
|[enable_if](../standard-library/enable-if-class.md)|如果条件为 true，则生成指定类型，否则不生成类型。|
|[result_of](../standard-library/result-of-class.md)|确定可调用类型的返回类型，该可调用类型采用指定参数类型。|
|[underlying_type](../standard-library/underlying-type-class.md)|生成枚举类型的基础整型类型。|

## <a name="see-also"></a>请参阅

[\<functional>](../standard-library/functional.md)<br/>
