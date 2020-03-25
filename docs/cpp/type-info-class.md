---
title: type_info 类
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 7a016fe8fee4e5765e6172184bfa9c90eecbc687
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160666"
---
# <a name="type_info-class"></a>type_info 类

**Type_info**类描述编译器在程序内生成的类型信息。 此类的对象可以有效存储指向类型的名称的指针。 **Type_info**类还存储了一个适合用于比较两个类型是否相等或排序的编码值。 类型的编码规则和排列顺序是未指定的，并且可能因程序而异。

必须包含 `<typeinfo>` 头文件才能使用**type_info**类。 **Type_info**类的接口是：

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

不能直接实例化**type_info**类的对象，因为该类只有一个私有复制构造函数。 构造（临时） **type_info**对象的唯一方法是使用[typeid](../cpp/typeid-operator.md)运算符。 由于赋值运算符也是私有的，因此不能复制或分配**type_info**类的对象。

`type_info::hash_code` 定义适用于将类型**typeinfo**的值映射到索引值分布的哈希函数。

运算符 `==` 和 `!=` 可用于分别比较是否与其他**type_info**对象比较是否相等。

类型的排列顺序与继承关系之间没有关联。 使用 `type_info::before` 成员函数确定类型的排序顺序。 不保证 `type_info::before` 在同一程序的不同程序或不同的运行中产生相同的结果。 通过这种方式，`type_info::before` 类似于 `(&)` 运算符的地址。

`type_info::name` 成员函数返回一个表示类型的用户可读名称的以 null 结尾的字符串的 `const char*`。 将缓存所指向的内存，应该从不直接释放它。

`type_info::raw_name` 成员函数返回一个表示对象类型的修饰名称的以 null 结尾的字符串的 `const char*`。 该名称实际上以其修饰的形式存储以节省空间。 因此，此函数比 `type_info::name` 更快，因为它不需要取消修饰名称。 `type_info::raw_name` 函数返回的字符串在比较运算中非常有用，但不可读。 如果需要用户可读的字符串，请改用 `type_info::name` 函数。

仅当指定了[/GR （启用运行时类型信息）](../build/reference/gr-enable-run-time-type-information.md)编译器选项时，才会为多态类生成类型信息。

## <a name="see-also"></a>另请参阅

[运行时类型信息](../cpp/run-time-type-information.md)
