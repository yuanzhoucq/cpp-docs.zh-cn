---
title: "basic_string 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_string"
  - "std::basic_string"
  - "basic_string"
  - "xstring/std::basic_string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_string 类"
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# basic_string 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由模板类 `basic_string` 的一个对象控制的序列是标准 C\+\+ 字符串类且通常作为字符串被引用，但不应将它们与以 null 结尾的通用于标准 C\+\+ 库的 C 样式字符串相混淆。  标准 C\+\+ 字符串是一个容器，它可使字符串作为普通类型使用，例如，比较和连接操作、迭代器、STL 算法以及复制由类分配器管理的内存和使用它进行分配。  如果你需要将标准 C\+\+ 字符串转换为以 null 结尾的 C 样式字符串，请使用 [basic\_string::c\_str](../Topic/basic_string::c_str.md) 成员。  
  
## 语法  
  
```  
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>> class basic_string;  
```  
  
#### 参数  
 `CharType`  
 要存储在字符串中的单个字符的数据类型。  标准 C\+\+ 库使用类型 `char` 的元素的类型定义 [string](../Topic/string%20\(C++%20STL%20%3Cstring%3E\).md)、类型 `wchar_t` 的元素的类型定义 [wstring](../Topic/wstring.md)、类型 `char16_t` 的元素的类型定义 [u16string](../Topic/u16string.md) 以及类型 `char32_t` 的元素的类型定义 [u32string](../Topic/u32string.md) 提供此模板类的专用化。  
  
 `Traits`  
 basic\_string 专用化中 **CharType** 元素的各种重要属性由类 **Traits** 描述。  默认值为 `char_traits`\<`CharType`\>。  
  
 `Allocator`  
 一种表示存储的分配器对象的类型，该分配器对象封装有关字符串的内存分配和解除分配的详细信息。  默认值为 **allocator**\<`CharType`\>。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_string](../Topic/basic_string::basic_string.md)|构建一个字符串，它为空或被特定字符初始化，或者是某个其他字符串对象或 C 字符串的全部或部分的副本。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_string::allocator_type.md)|表示字符串对象的 `allocator` 类的类型。|  
|[const\_iterator](../Topic/basic_string::const_iterator.md)|提供可访问和读取字符串中 `const` 元素的随机访问迭代器的类型。|  
|[const\_pointer](../Topic/basic_string::const_pointer.md)|提供指向字符串中 `const` 元素的指针的类型。|  
|[const\_reference](../Topic/basic_string::const_reference.md)|提供对存储于字符串中供读取和执行 `const` 操作的 `const` 元素的引用的类型。|  
|[const\_reverse\_iterator](../Topic/basic_string::const_reverse_iterator.md)|提供可访问字符串中任何 `const` 元素的随机访问迭代器的类型。|  
|[difference\_type](../Topic/basic_string::difference_type.md)|提供引用同一字符串中的元素的两个迭代器之间的差异的类型。|  
|[iterator](../Topic/basic_string::iterator.md)|提供可读取或修改字符串中任何元素的随机访问迭代器的类型。|  
|[npos](../Topic/basic_string::npos.md)|一个初始化为 –1 的无符号整数值，这个值在搜索功能失败时指示“找不到”或“所有其余字符”。|  
|[指针](../Topic/basic_string::pointer.md)|提供指向字符串中或字符数组中字符元素的指针的类型。|  
|[reference](../Topic/basic_string::reference.md)|提供对存储在字符串中的元素的引用的类型。|  
|[reverse\_iterator](../Topic/basic_string::reverse_iterator.md)|提供可读取或修改反向字符串中元素的随机访问迭代器的类型。|  
|[size\_type](../Topic/basic_string::size_type.md)|字符串中元素的数目的无符号整数类型。|  
|[traits\_type](../Topic/basic_string::traits_type.md)|存储在字符串中的元素的字符特征的一个类型。|  
|[value\_type](../Topic/basic_string::value_type.md)|表示存储在字符串中的字符的类型的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[append](../Topic/basic_string::append.md)|向字符串的末尾添加字符。|  
|[assign](../Topic/basic_string::assign.md)|对字符串的内容赋新的字符值。|  
|[at](../Topic/basic_string::at.md)|返回对字符串中指定位置的元素的引用。|  
|[back](../Topic/basic_string::back.md)||  
|[begin](../Topic/basic_string::begin.md)|返回发现字符串中第一个元素的位置的迭代器。|  
|[c\_str](../Topic/basic_string::c_str.md)|将字符串的内容转换为以 null 结尾的 C 样式字符串。|  
|[capacity](../Topic/basic_string::capacity.md)|返回在不增加字符串内存分配的情况下可存储在字符串中的元素的最大数目。|  
|[cbegin](../Topic/basic_string::cbegin.md)|返回发现字符串中第一个元素的位置的常量迭代器。|  
|[cend](../Topic/basic_string::cend.md)|返回发现字符串中最后一个元素之后的位置的常量迭代器。|  
|[clear](../Topic/basic_string::clear.md)|清除字符串中的全部元素。|  
|[compare](../Topic/basic_string::compare.md)|将字符串与指定字符串比较，确定两个字符串是否相等或按字典顺序一个字符串是否小于另一个。|  
|[copy](../Topic/basic_string::copy.md)|将指定数目的字符从源字符串中的索引位置复制到目标字符组。  已否决。  请改用 [basic\_string::\_Copy\_s](../Topic/basic_string::_Copy_s.md)。|  
|[crbegin](../Topic/basic_string::crbegin.md)|返回发现反向字符串中第一个元素的位置的常量迭代器。|  
|[crend](../Topic/basic_string::crend.md)|返回发现反向字符串中最后一个元素之后的位置的常量迭代器。|  
|[\_Copy\_s](../Topic/basic_string::_Copy_s.md)|将指定数目的字符从源字符串中的索引位置复制到目标字符组。|  
|[数据](../Topic/basic_string::data.md)|将字符串的内容转换为字符数组。|  
|[empty](../Topic/basic_string::empty.md)|测试字符串是否包含字符。|  
|[end](../Topic/basic_string::end.md)|返回发现字符串中最后一个元素之后的位置的迭代器。|  
|[erase](../Topic/basic_string::erase.md)|从字符串中的指定位置删除一个或一系列元素。|  
|[find](../Topic/basic_string::find.md)|向前搜索字符串，搜索与指定字符序列匹配的第一个子字符串。|  
|[find\_first\_not\_of](../Topic/basic_string::find_first_not_of.md)|在字符串中搜索不属于指定字符串中元素的第一个字符。|  
|[find\_first\_of](../Topic/basic_string::find_first_of.md)|在字符串中搜索与指定字符串中任何元素匹配的第一个字符。|  
|[find\_last\_not\_of](../Topic/basic_string::find_last_not_of.md)|在字符串中搜索不属于指定字符串中任何元素的最后一个字符。|  
|[find\_last\_of](../Topic/basic_string::find_last_of.md)|在字符串中搜索属于指定字符串中一个元素的最后一个字符。|  
|[front](../Topic/basic_string::front.md)|返回对字符串中第一个元素的引用。|  
|[get\_allocator](../Topic/basic_string::get_allocator.md)|返回用于构造字符串的 `allocator` 对象的副本。|  
|[insert](../Topic/basic_string::insert.md)|将一个、多个或一些列元素插入字符串中的指定位置。|  
|[length](../Topic/basic_string::length.md)|返回字符串中元素的当前数目。|  
|[max\_size](../Topic/basic_string::max_size.md)|返回字符串可包含的字符的最大数目。|  
|[pop\_back](../Topic/basic_string::pop_back.md)|删除字符串的最后一个元素。|  
|[push\_back](../Topic/basic_string::push_back.md)|在字符串的末尾处添加一个元素。|  
|[rbegin](../Topic/basic_string::rbegin.md)|返回指向反向字符串中第一个元素的迭代器。|  
|[rend](../Topic/basic_string::rend.md)|返回指向刚超出反向字符串的最后一个元素的位置的迭代器。|  
|[replace](../Topic/basic_string::replace.md)|用指定字符或者从其他范围、字符串或 C 字符串复制的字符来替代字符串中指定位置的元素。|  
|[reserve](../Topic/basic_string::reserve.md)|将字符串的容量设置为一个数目，这个数目至少应与指定数目一样大。|  
|[resize](../Topic/basic_string::resize.md)|根据要求追加或删除元素，为字符串指定新的大小。|  
|[rfind](../Topic/basic_string::rfind.md)|向后搜索字符串，搜索与指定字符序列匹配的第一个子字符串。|  
|[shrink\_to\_fit](../Topic/basic_string::shrink_to_fit.md)|放弃字符串的超出容量。|  
|[size](../Topic/basic_string::size.md)|返回字符串中元素的当前数目。|  
|[substr](../Topic/basic_string::substr.md)|从字符串起始处的指定位置复制最多某个数目的字符的子字符串。|  
|[swap](../Topic/basic_string::swap.md)|交换两个字符串的内容。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 \+\=](../Topic/basic_string::operator+=.md)|向字符串追加字符。|  
|[operator \=](../Topic/basic_string::operator=.md)|对字符串的内容赋新的字符值。|  
|[operator&#91;&#93;](../Topic/basic_string::operator.md)|使用字符串中的指定索引提供对字符的引用。|  
  
## 备注  
 如果要求函数生成的序列长于 [max\_size](../Topic/basic_string::max_size.md) 元素，这个函数将通过引发 [length\_error](../standard-library/length-error-class.md) 类型的对象来报告长度错误。  
  
 用于指定受控制序列元素的引用、指针和迭代器在调用了可更改受控制序列的函数后或第一次调用一个非 **const** 成员函数后可能失效。  
  
## 要求  
 **标头：**\<string\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<string\>](../standard-library/string.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)