---
title: type_info 类
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: b0cddd2c5cc09e77e8733ca88177c3b2223fc8ce
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68242088"
---
# <a name="typeinfo-class"></a>type_info 类

**Type_info**类描述在程序中由编译器生成的类型信息。 此类的对象可以有效存储指向类型的名称的指针。 **Type_info**类还可存储适合比较是否相等的两个类型或比较其排列顺序的编码的值。 类型的编码规则和排列顺序是未指定的，并且可能因程序而异。

`<typeinfo>`标头文件必须包含要使用**type_info**类。 接口**type_info**类是：

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

无法实例化的对象**type_info**类直接，因为该类只有一个私有复制构造函数。 构造 （临时） 的唯一办法**type_info**对象是使用[typeid](../cpp/typeid-operator.md)运算符。 由于赋值运算符也是私有的不能复制或分配类的对象**type_info**。

`type_info::hash_code` 定义适用于类型的值映射的哈希函数**typeinfo**到索引值的分布。

运算符`==`并`!=`可用于与其他比较是否相等**type_info**对象，分别。

类型的排列顺序与继承关系之间没有关联。 使用`type_info::before`成员函数以确定类型的排序规则顺序。 不能保证的`type_info::before`将产生不同的程序或甚至运行在同一程序中相同的结果。 以这种方式`type_info::before`类似于 address-of`(&)`运算符。

`type_info::name`成员函数返回`const char*`为以 null 结尾的字符串表示的用户可读名称的类型。 将缓存所指向的内存，应该从不直接释放它。

`type_info::raw_name`成员函数返回`const char*`为以 null 结尾的字符串表示的对象类型的修饰的名。 该名称实际上以其修饰的形式存储以节省空间。 因此，此函数是比要快`type_info::name`因为它不需要取消修饰名称。 返回的字符串`type_info::raw_name`函数在比较操作很有用，但不可读。 如果你需要的可读的字符串，使用`type_info::name`函数。

为多态类才生成类型信息[/GR （启用运行时类型信息）](../build/reference/gr-enable-run-time-type-information.md)指定编译器选项。

## <a name="see-also"></a>请参阅

[运行时类型信息](../cpp/run-time-type-information.md)