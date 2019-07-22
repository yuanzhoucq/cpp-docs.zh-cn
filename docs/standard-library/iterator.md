---
title: '&lt;Iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: f859c2e11d8a800c44b93e69e4b862300c6d3a13
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245767"
---
# <a name="ltiteratorgt"></a>&lt;Iterator&gt;

定义迭代器基元、预定义的迭代器和流迭代器，以及一些支持模板。 预定义的迭代器包含插入及反向适配器。 插入迭代器适配器包括三类：前向、后向和常规。 它们提供的是插入语义而不是容器成员函数迭代器所提供的覆盖语义。

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间：** std

## <a name="remarks"></a>备注

迭代器是指针的泛化，它从这些指针的需求中抽象出来，允许 C++ 程序使用统一的方式来处理不同的数据结构。 迭代器充当容器和泛型算法之间的媒介。 算法被定义为对某一迭代器类型所指定的范围起作用，而不是作用于特定的数据类型。 随后，算法可能会作用于任何满足迭代器要求的数据结构。 迭代器有五个类型或类别，各自具有自己的要求和最终功能：

- 输出：向前移动，可以存储但不能检索值，由 ostream 和 inserter 提供。

- 输入：向前移动，可以检索但不能存储值，由 istream 提供。

- 向前：向前移动，可以存储和检索值。

- 双向：向前和向后移动，可以存储和检索值，由列表、集合、多重集、映射和多重映射提供。

- 随机访问：以任意顺序访问元素，可以存储和检索值，由向量、双端队列、字符串和数组提供。

可使用要求较高、因而需要更强大元素访问的迭代器来代替要求较低的迭代器。 例如，如果调用向前迭代器，则可使用随机访问迭代器来代替。

Visual Studio 为 C++ 标准库迭代器增加了一些扩展，以便支持多种检查迭代器和未检查迭代器的调试模式情形。 有关详细信息，请参阅[安全库：C++标准库](../standard-library/safe-libraries-cpp-standard-library.md)。

## <a name="members"></a>成员

### <a name="functions"></a>函数

|||
|-|-|
|[advance](../standard-library/iterator-functions.md#advance)|使迭代器递增指定数量的位置。|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|创建一个可以在指定容器的后面插入元素的迭代器。|
|[begin](../standard-library/iterator-functions.md#begin)|检索一个指向指定容器中第一个元素的迭代器。|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|检索一个指向指定容器中第一个元素的常量迭代器。|
|[cend](../standard-library/iterator-functions.md#cend)|检索一个指向指定容器中最后元素之后的元素的常量迭代器。|
|[crbegin](../standard-library/iterator-functions.md#crbegin)||
|[crend](../standard-library/iterator-functions.md#crend)||
|[data](../standard-library/iterator-functions.md#data)||
|[distance](../standard-library/iterator-functions.md#distance)|确定两个迭代器定址位置之间的增量数。|
|[end](../standard-library/iterator-functions.md#end)|检索指向指定容器中最后一个元素之后的元素的迭代器。|
|[empty](../standard-library/iterator-functions.md#empty)||
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|创建一个可以在指定容器前面插入元素的迭代器。|
|[inserter](../standard-library/iterator-functions.md#inserter)|一个可以在指定插入点向容器添加新元素的迭代器适配器。|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|创建可由其他算法使用的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。 **注意：** 该函数是 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|返回一个移动迭代器，其中包含所提供的迭代器作为其存储的基迭代器。|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|创建可由其他算法使用的 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。 **注意：** 该函数是 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|
|[next](../standard-library/iterator-functions.md#next)|迭代指定的次数并返回新的迭代器位置。|
|[prev](../standard-library/iterator-functions.md#prev)|反向迭代指定的次数并返回新的迭代器位置。|
|[rbegin](../standard-library/iterator-functions.md#rbegin)||
|[rend](../standard-library/iterator-functions.md#rend)||
|[size](../standard-library/iterator-functions.md#size)||

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](../standard-library/iterator-operators.md#op_neq)|测试运算符左侧的迭代器对象是否不等于右侧的迭代器对象。|
|[operator==](../standard-library/iterator-operators.md#op_eq_eq)|测试运算符左侧的迭代器对象是否等于右侧的迭代器对象。|
|[operator<](../standard-library/iterator-operators.md#op_lt)|测试运算符左侧的迭代器对象是否小于右侧的迭代器对象。|
|[operator\<=](../standard-library/iterator-operators.md#op_gt_eq)|测试运算符左侧的迭代器对象是否小于或等于右侧的迭代器对象。|
|[operator>](../standard-library/iterator-operators.md#op_gt)|测试运算符左侧的迭代器对象是否大于右侧的迭代器对象。|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|测试运算符左侧的迭代器对象是否大于或等于右侧的迭代器对象。|
|[operator+](../standard-library/iterator-operators.md#op_add)|将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。|
|[operator-](../standard-library/iterator-operators.md#operator-)|从另一个迭代器中减去一个迭代器并返回差值。|

### <a name="classes"></a>类

|||
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|此模板类描述输出迭代器对象。 它将元素插入到类型的容器`Container`，通过受保护访问`pointer`对象将存储在名为容器。|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|一个类，提供返回类型的`iterator_category`表示双向迭代器函数。|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|一种使用随机访问检查迭代器来访问数组的类。 **注意：** 此类为 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|一个类，提供返回类型的`iterator_category`表示前向迭代器函数。|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|此模板类描述输出迭代器对象。 它将元素插入到类型的容器`Container`，通过受保护访问`pointer`对象将存储在名为容器。|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|一个类，提供返回类型的`iterator_category`代表输入迭代器的函数。|
|[insert_iterator](../standard-library/insert-iterator-class.md)|此模板类描述输出迭代器对象。 它将元素插入到类型的容器`Container`，通过受保护访问`pointer`对象将存储在名为容器。 它还存储受保护`iterator`类的对象`Container::iterator`称为`iter`。|
|[istream_iterator](../standard-library/istream-iterator-class.md)|此模板类描述输入迭代器对象。 它提取类的对象`Ty`从输入流，通过其存储的指针类型的对象访问`basic_istream` \< **Elem**， **Tr**>。|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|此模板类描述输入迭代器对象。 它将这些类的元素插入`Elem`到输出流缓冲区，并通过的对象访问其存储的类型、`pointer`到`basic_streambuf` \< **Elem**， **Tr**>。|
|[Iterator](../standard-library/iterator-struct.md)|模板类用作所有迭代器的基类型。|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|一种模板 helper 类，可以提供与不同迭代器类型相关联的关键类型，以便用相同的方式引用这些迭代器。|
|[move_iterator](../standard-library/move-iterator-class.md)|`move_iterator` 对象可以存储 `RandomIterator` 类型的随机访问迭代器。 它的行为类似于随机访问迭代器，但在解引用时除外。 `operator*` 的结果将隐式强制转换为 `value_type&&:`，以便形成 `rvalue reference`。|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|此模板类描述输出迭代器对象。 这类对象插入`Type`到输出流，并通过的对象访问其存储的类型、`pointer`到`basic_ostream` \< **Elem**， **Tr**>。|
|[ostreambuf_iterator 类](../standard-library/ostreambuf-iterator-class.md)|此模板类描述输出迭代器对象。 它将这些类的元素插入`Elem`到输出流缓冲区，通过它存储到指针类型的对象访问`basic_streambuf` \< **Elem**， **Tr**>。|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|一个类，提供返回类型的`iterator_category`代表输出迭代器的函数。|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|一个类，提供返回类型的`iterator_category`代表随机访问迭代器的函数。|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|此模板类描述一个行为类似于随机访问迭代器的对象，只不过方向相反。|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|一种使用随机访问未检查迭代器来访问数组的类。 **注意：** 此类为 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
