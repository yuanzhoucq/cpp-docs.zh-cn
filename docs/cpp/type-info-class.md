---
title: type_info 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- type_info
dev_langs:
- C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3e3138c9028f72327c9d4bf2c2f2e82c942dbde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422431"
---
# <a name="typeinfo-class"></a>type_info 类
**Type_info**类描述编译器在程序中生成的类型信息。 此类的对象可以有效存储指向类型的名称的指针。 **Type_info**类还可存储适合比较是否相等的两个类型或比较其排列顺序的编码的值。 类型的编码规则和排列顺序是未指定的，并且可能因程序而异。  
  
 `<typeinfo>`标头文件必须包含为了使用**type_info**类。 接口**type_info**类是：  
  
```cpp
class type_info {  
public:  
    virtual ~type_info();  
    size_t hash_code() const  
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;  
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;  
    _CRTIMP_PURE int before(const type_info& rhs) const;  
    _CRTIMP_PURE const char* name() const;  
    _CRTIMP_PURE const char* raw_name() const;  
};  
```  
  
 无法实例化的对象**type_info**类直接，因为此类具有一个私有复制构造函数。 构造 （临时） 的唯一办法**type_info**对象是使用[typeid](../cpp/typeid-operator.md)运算符。 由于赋值运算符也是私有的无法复制或分配类的对象**type_info**。  
  
 **type_info:: hash_code**定义适合映射类型的值的哈希函数**typeinfo**索引值的分布。  
  
 运算符`==`和`!=`可用来与其他比较是否相等和不相等**type_info**对象，分别。  
  
 类型的排列顺序与继承关系之间没有关联。 使用**type_info**成员函数来确定类型的排序顺序。 不能保证， **type_info**将生成不同的程序或甚至不同运行同一程序中相同的结果。 这种方式， **type_info**类似于地址的 **(&)** 运算符。  
  
 **Type_info:: name**成员函数将返回**const char\*** 以 null 结尾的字符串表示的用户可读名称的类型。 将缓存所指向的内存，应该从不直接释放它。  
  
 **Type_info:: raw_name**成员函数将返回**const char\*** 以 null 结尾的字符串表示的修饰的名称的对象类型。 该名称实际上以其修饰的形式存储以节省空间。 因此，此函数是比快**type_info:: name**因为它不需要取消修饰名称。 返回的字符串**type_info:: raw_name**函数是比较操作中有用，但不是可读。 如果你需要的用户可读的字符串，使用**type_info:: name**函数。  
  
 为多态类才生成类型信息[/GR （启用运行时类型信息）](../build/reference/gr-enable-run-time-type-information.md)指定编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)
