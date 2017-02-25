---
title: "&lt;type_traits&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<type_traits>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typetrait 标头 [TR1]"
  - "type_traits"
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
caps.latest.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 35
---
# &lt;type_traits&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义了提供编译时常数为提供有关其类型参数的属性的信息或生成转换类型的模板。  
  
## 语法  
  
```  
#include <type_traits>  
```  
  
## 备注  
 类和中的模板 `<type_traits>` 用于支持类型推断、 分类和在编译时间，以检测与类型相关的错误，并帮助您优化泛型代码转换。 这些类和模板包括一元类型特征，用于描述一个类型的属性描述类型和修改属性的一种类型的转换特征之间的关系的二进制类型特征。  
  
 若要支持类型特征，帮助器类 `integral_constant`, ，定义。 它具有模板专用化 `true_type` 和 `false_type` 构成类型谓词的基类。 一个 *类型谓词* 是采用一个或多个类型参数的模板。 如果类型谓词*保留为 true*，则它是以公共方式直接或间接从 [true\_type](../Topic/true_type%20Typedef.md) 派生的。 如果类型谓词*保留为 false*，则它是以公共方式直接或间接从 [false\_type](../Topic/false_type%20Typedef.md) 派生的。  
  
 一个 *类型修饰符* 或 *转换特征* 是采用一个或多个模板参数的模板，并且有一个成员 `type`, ，这是在修改的类型的同义词。  
  
### 别名模板  
 若要简化类型特征表达式 [别名模板](../cpp/aliases-and-typedefs-cpp.md) 为 `typename some_trait<T>::type` 提供，其中" `some_trait`"是模板类名称。 例如， [add\_const](../standard-library/add-const-class.md) 具有其类型的别名模板 `add_const_t`, ，其定义如下︰  
  
```cpp  
template<class T>  
    using add_const_t = typename add_const<T>::type;  
```  
  
|||||  
|-|-|-|-|  
|add\_const\_t|aligned\_storage\_t|make\_signed\_t|remove\_pointer\_t|  
|add\_cv\_t|aligned\_union\_t|make\_unsigned\_t|remove\_reference\_t|  
|add\_lvalue\_reference\_t|common\_type\_t|remove\_all\_extents\_t|remove\_volatile\_t|  
|add\_pointer\_t|conditional\_t|remove\_const\_t|result\_of\_t|  
|add\_rvalue\_reference\_t|decay\_t|remove\_cv\_t|underlying\_type\_t|  
|add\_volatile\_t|enable\_if\_t|remove\_extent\_t||  
  
### 类  
 帮助器类和 typedef  
  
|||  
|-|-|  
|[integral\_constant](../standard-library/integral-constant-class-bool-constant-class.md)|从类型和值设置整型常量。|  
|[true\_type](../Topic/true_type%20Typedef.md)|保留包含值 true 的整数常量。|  
|[false\_type](../Topic/false_type%20Typedef.md)|保留包含值 false 的整数常量。|  
  
 主要类型类别  
  
|||  
|-|-|  
|[is\_void](../standard-library/is-void-class.md)|测试类型是否为 `void`。|  
|[is\_null\_pointer](../standard-library/is-null-pointer-class.md)|测试类型是否为 `std::nullptr_t`。|  
|[is\_integral](../standard-library/is-integral-class.md)|测试类型是否为整型。|  
|[is\_floating\_point](../standard-library/is-floating-point-class.md)|测试类型是否为浮点。|  
|[is\_array](../standard-library/is-array-class.md)|测试类型是否为数组。|  
|[is\_pointer](../standard-library/is-pointer-class.md)|测试类型是否为指针。|  
|[is\_lvalue\_reference](../standard-library/is-lvalue-reference-class.md)|测试类型是否是左值引用。|  
|[is\_rvalue\_reference](../standard-library/is-rvalue-reference-class.md)|测试类型是否是右值引用。|  
|[is\_member\_object\_pointer](../standard-library/is-member-object-pointer-class.md)|测试类型是否为指向成员对象的指针。|  
|[is\_member\_function\_pointer](../standard-library/is-member-function-pointer-class.md)|测试类型是否为指向成员函数的指针。|  
|[is\_enum](../standard-library/is-enum-class.md)|测试类型是否为枚举。|  
|[is\_union](../standard-library/is-union-class.md)|测试类型是否为联合。|  
|[is\_class](../standard-library/is-class-class.md)|测试类型是否为类。|  
|[is\_function](../standard-library/is-function-class.md)|测试类型是否为函数类型。|  
  
 复合类型类别  
  
|||  
|-|-|  
|[is\_reference](../standard-library/is-reference-class.md)|测试类型是否为引用。|  
|[is\_arithmetic](../standard-library/is-arithmetic-class.md)|测试类型是否为算术型。|  
|[is\_fundamental](../standard-library/is-fundamental-class.md)|测试类型是否为 `void` 或算术型。|  
|[is\_object](../standard-library/is-object-class.md)|测试类型是否为对象类型。|  
|[is\_scalar](../standard-library/is-scalar-class.md)|测试类型是否为标量类型。|  
|[is\_compound](../standard-library/is-compound-class.md)|测试类型是否为非标量类型。|  
|[is\_member\_pointer](../standard-library/is-member-pointer-class.md)|测试类型是否为指向成员的指针。|  
  
 类型属性  
  
|||  
|-|-|  
|[is\_const](../standard-library/is-const-class.md)|测试类型是否为 `const`。|  
|[is\_volatile](../standard-library/is-volatile-class.md)|测试类型是否为 `volatile`。|  
|[is\_trivial](../standard-library/is-trivial-class.md)|测试类型是否为简单。|  
|[is\_trivially\_copyable](../standard-library/is-trivially-copyable-class.md)|测试类型是否为完全复制。|  
|[is\_standard\_layout](../standard-library/is-standard-layout-class.md)|测试类型是否为标准布局类型。|  
|[is\_pod](../standard-library/is-pod-class.md)|测试类型是否为 POD。|  
|[is\_literal\_type](../standard-library/is-literal-type-class.md)|测试是否的类型可以是 `constexpr` 变量或用在 `constexpr` 函数。|  
|[is\_empty](../standard-library/is-empty-class.md)|测试类型是否为空类。|  
|[is\_polymorphic](../standard-library/is-polymorphic-class.md)|测试类型是否为多态类。|  
|[is\_abstract](../standard-library/is-abstract-class.md)|测试类型是否为抽象类。|  
|[is\_final](../standard-library/is-final-class.md)|测试类型是否为标记的类类型 `final`。|  
|[is\_signed](../standard-library/is-signed-class.md)|测试类型是否为有符号的整数。|  
|[is\_unsigned](../standard-library/is-unsigned-class.md)|测试类型是否为无符号的整数。|  
|[is\_constructible](../standard-library/is-constructible-class.md)|测试类型是否为可构造使用指定的参数类型。|  
|[is\_default\_constructible](../standard-library/is-default-constructible-class.md)|测试类型是否包含一个默认构造函数。|  
|[is\_copy\_constructible](../standard-library/is-copy-constructible-class.md)|测试类型是否包含一个复制构造函数。|  
|[is\_move\_constructible](../standard-library/is-move-constructible-class.md)|测试类型是否包含移动构造函数。|  
|[is\_assignable](../standard-library/is-assignable-class.md)|测试是否第一种类型都可以分配到第二个类型的值。|  
|[is\_copy\_assignable](../standard-library/is-copy-assignable-class.md)|测试是否可以指定一个类型的类型的常量引用值。|  
|[is\_move\_assignable](../standard-library/is-move-assignable-class.md)|测试是否可以指定一个类型的右值引用的类型。|  
|[is\_destructible](../standard-library/is-destructible-class.md)|测试该类型是否易损坏。|  
|[is\_trivially\_constructible](../standard-library/is-trivially-constructible-class.md)|测试是否不使用任何重要的操作时使用的指定的类型构造的类型。|  
|[is\_trivially\_default\_constructible](../standard-library/is-trivially-default-constructible-class.md)|测试是否不使用任何重要的操作类型默认构造时。|  
|[is\_trivially\_copy\_constructible](../standard-library/is-trivially-copy-constructible-class.md)|测试是否复制构造时不使用任何重要的操作类型。|  
|[is\_trivially\_move\_constructible](../standard-library/is-trivially-move-constructible-class.md)|测试是否移动构造时不使用任何重要的操作类型。|  
|[is\_trivially\_assignable](../standard-library/is-trivially-assignable-class.md)|测试是否可分配的类型赋值不使用任何重要的操作。|  
|[is\_trivially\_copy\_assignable](../standard-library/is-trivially-copy-assignable-class.md)|测试类型是否是可赋值的复制和赋值使用任何重要的操作。|  
|[is\_trivially\_move\_assignable](../standard-library/is-trivially-move-assignable-class.md)|测试类型是否是可赋值的移动和分配使用任何重要的操作。|  
|[is\_trivially\_destructible](../standard-library/is-trivially-destructible-class.md)|测试类型易损坏以及析构函数使用任何重要的操作。|  
|[is\_nothrow\_constructible](../standard-library/is-nothrow-constructible-class.md)|测试类型可构造，以及已知不在构造使用指定的类型时引发。|  
|[is\_nothrow\_default\_constructible](../standard-library/is-nothrow-default-constructible-class.md)|测试类型是否为默认构造和已知没有默认构造时引发。|  
|[is\_nothrow\_copy\_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|测试是否类型是复制构造的并且复制构造函数已知不引发。|  
|[is\_nothrow\_move\_constructible](../standard-library/is-nothrow-move-constructible-class.md)|测试类型移动构造，以及移动构造函数已知不引发。|  
|[is\_nothrow\_assignable](../standard-library/is-nothrow-assignable-class.md)|测试类型可使用指定的类型赋值以及分配已知不引发。|  
|[is\_nothrow\_copy\_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|测试类型可分配的副本以及分配已知不引发。|  
|[is\_nothrow\_move\_assignable](../standard-library/is-nothrow-move-assignable-class.md)|测试类型移动赋值以及分配已知不引发。|  
|[is\_nothrow\_destructible](../standard-library/is-nothrow-destructible-class.md)|测试类型易损坏以及析构函数已知不引发。|  
|[has\_virtual\_destructor](http://msdn.microsoft.com/zh-cn/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|测试类型是否包含虚拟的析构函数。|  
  
 类型属性查询  
  
|||  
|-|-|  
|[alignment\_of](../standard-library/alignment-of-class.md)|获取类型的对齐方式。|  
|[rank](../standard-library/rank-class.md)|获取数组维度数。|  
|[extent](../standard-library/extent-class.md)|获取指定的数组维度中的元素数。|  
  
 类型关系  
  
|||  
|-|-|  
|[is\_same](../standard-library/is-same-class.md)|确定两个类型是否相同。|  
|[is\_base\_of](../standard-library/is-base-of-class.md)|测试是否是一种类型的另一个基。|  
|[is\_convertible](../standard-library/is-convertible-class.md)|测试一种类型是否可转换为另一种类型。|  
  
 Const 易失性的修改  
  
|||  
|-|-|  
|[add\_const](../standard-library/add-const-class.md)|生成 `const` 从类型的类型。|  
|[add\_volatile](../standard-library/add-volatile-class.md)|生成 `volatile` 从类型的类型。|  
|[add\_cv](../standard-library/add-cv-class.md)|生成 `const``volatile` 从类型的类型。|  
|[remove\_const](../standard-library/remove-const-class.md)|生成类型中的非常量类型。|  
|[remove\_volatile](../standard-library/remove-volatile-class.md)|生成类型的非易失性类型。|  
|[remove\_cv](../standard-library/remove-cv-class.md)|生成类型的非 const 非易失性类型。|  
  
 引用的修改  
  
|||  
|-|-|  
|[add\_lvalue\_reference](../standard-library/add-lvalue-reference-class.md)|生成类型从类型的引用。|  
|[add\_rvalue\_reference](../standard-library/add-rvalue-reference-class.md)|生成要类型从指向类型的右值引用|  
|[remove\_reference](../standard-library/remove-reference-class.md)|生成类型的非引用类型。|  
  
 符号修改  
  
|||  
|-|-|  
|[make\_signed](../standard-library/make-signed-class.md)|生成的类型，如果已签名或最小的有符号的类型大于或等于大小类型。|  
|[make\_unsigned](../standard-library/make-unsigned-class.md)|生成的类型，如果未签名或最小无符号的类型大于或等于大小类型。|  
  
 数组的修改  
  
|||  
|-|-|  
|[remove\_all\_extents](../standard-library/remove-all-extents-class.md)|将生成从数组类型的非数组类型。|  
|[remove\_extent](../standard-library/remove-extent-class.md)|生成从数组类型的元素类型。|  
  
 指针的修改  
  
|||  
|-|-|  
|[add\_pointer](../standard-library/add-pointer-class.md)|将生成指向类型从类型的指针。|  
|[remove\_pointer](../standard-library/remove-pointer-class.md)|将生成一个指针，要键入的类型。|  
  
 其他转换  
  
|||  
|-|-|  
|[aligned\_storage](../standard-library/aligned-storage-class.md)|为对齐类型分配未初始化的内存。|  
|[aligned\_union](../standard-library/aligned-union-class.md)|为具有不常用构造函数或析构函数的对齐联合分配未初始化的内存。|  
|[common\_type](../standard-library/common-type-class.md)|生成的参数包的所有类型的公共类型。|  
|[conditional](../standard-library/conditional-class.md)|如果条件为真，将生成第一个指定的类型，否则第二个指定的类型。|  
|[decay](../standard-library/decay-class.md)|所传递的值，则生成的类型。 设置非引用、非常量或非可变类型或者设置指向类型的指针。|  
|[enable\_if](../standard-library/enable-if-class.md)|如果条件为真，将生成指定的类型，否则没有类型。|  
|[result\_of](../standard-library/result-of-class1.md)|确定采用指定的参数类型的可调用类型的返回类型。|  
|[underlying\_type](../standard-library/underlying-type-class.md)|生成枚举类型的基础整数的类型。|  
  
## 请参阅  
 [\<functional\>](../standard-library/functional.md)