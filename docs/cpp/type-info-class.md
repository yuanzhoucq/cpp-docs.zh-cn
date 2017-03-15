---
title: "type_info 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "type_info"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 type_info"
  - "type_info 类"
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# type_info 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**type\_info** 类描述编译器在程序中生成的类型信息。  此类的对象可以有效存储指向类型的名称的指针。  **type\_info** 类还可存储适合比较两个类型是否相等或比较其排列顺序的编码值。  类型的编码规则和排列顺序是未指定的，并且可能因程序而异。  
  
 必须包含 \<`typeinfo>` 标头文件才能使用 **type\_info** 类。  **type\_info** 类的接口是：  
  
```  
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
  
 您不能直接实例化 **type\_info** 类的对象，因为该类只有一个私有复制构造函数。  构造（临时）**type\_info** 对象的唯一方式是使用 [typeid](../cpp/typeid-operator.md) 运算符。  由于赋值运算符也是私有的，因此不能复制或分配类 **type\_info** 的对象。  
  
 **type\_info::hash\_code** 可定义适合将 **typeinfo** 类型的值映射到索引值的分布的哈希函数。  
  
 运算符 `==` 和 `!=` 分别用于与其他 **type\_info** 对象比较是否相等和不相等。  
  
 类型的排列顺序与继承关系之间没有关联。  使用 **type\_info::before** 成员函数可确定类型的排序顺序。  不能保证 **type\_info::before** 在不同的程序中（甚至是多次运行同一程序时）会产生相同的结果。  这样，**type\_info::before** 类似于 address\-of **\(&\)** 运算符。  
  
 **type\_info::name** 成员函数可将 **const char\*** 返回到以 null 结尾的字符串，该字符串表示类型的用户可读名称。  将缓存所指向的内存，应该从不直接释放它。  
  
 **type\_info::raw\_name** 成员函数可将 **const char\*** 返回到以 null 结尾的字符串，该字符串表示对象类型的修饰名称。  该名称实际上以其修饰的形式存储以节省空间。  因此，此函数比 **type\_info::name** 更快，因为它不需要取消修饰名称。  **type\_info::raw\_name** 函数返回的字符串在比较运算符中很有用，但它不可读。  如果您需要用户可读的字符串，请改用 **type\_info::name** 函数。  
  
 仅当指定了 [\/GR（启用运行时类型信息）](../build/reference/gr-enable-run-time-type-information.md)编译器选项时，才会为多态类生成类型信息。  
  
## 请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)