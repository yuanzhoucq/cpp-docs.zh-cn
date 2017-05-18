---
title: '&lt;iterator&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<iterator>
- std.<iterator>
- <iterator>
- iterator/std::<iterator>
dev_langs:
- C++
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 67ba9e9a670ac187d15fe53729d8cdac475472ce
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;
定义迭代器基元、预定义的迭代器和流迭代器，以及一些支持模板。 预定义的迭代器包含插入及反向适配器。 插入迭代器适配器包括三类：前向、后向和常规。 它们提供的是插入语义而不是容器成员函数迭代器所提供的覆盖语义。  
  
## <a name="syntax"></a>语法  
  
```  
#include <iterator>  
  
```  
  
## <a name="remarks"></a>备注  
 迭代器是指针的泛化，它从这些指针的需求中抽象出来，允许 C++ 程序使用统一的方式来处理不同的数据结构。 迭代器充当容器和泛型算法之间的媒介。 算法被定义为对某一迭代器类型所指定的范围起作用，而不是作用于特定的数据类型。 随后，算法可能会作用于任何满足迭代器要求的数据结构。 迭代器有五个类型或类别，各自具有自己的要求和最终功能：  
  
-   输出：向前移动，可以存储但不能检索值，由 ostream 和 inserter 提供。  
  
-   输入：向前移动，可以检索但不能存储值，由 istream 提供。  
  
-   向前：向前移动，可以存储和检索值。  
  
-   双向：向前和向后移动，可以存储和检索值，由列表、集合、多重集、映射和多重映射提供。  
  
-   随机访问：以任意顺序访问元素，可以存储和检索值，由向量、双端队列、字符串和数组提供。  
  
 可使用要求较高、因而需要更强大元素访问的迭代器来代替要求较低的迭代器。 例如，如果调用向前迭代器，则可使用随机访问迭代器来代替。  
  
 Visual Studio 为 C++ 标准库迭代器增加了一些扩展，以便支持多种检查迭代器和未检查迭代器的调试模式情形。 有关详细信息，请参阅[安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)。  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[advance](../standard-library/iterator-functions.md#advance)|使迭代器递增指定数量的位置。|  
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|创建一个可以在指定容器的后面插入元素的迭代器。|  
|[begin](../standard-library/iterator-functions.md#begin)|检索一个指向指定容器中第一个元素的迭代器。|  
|[cbegin](../standard-library/iterator-functions.md#cbegin)|检索一个指向指定容器中第一个元素的常量迭代器。|  
|[cend](../standard-library/iterator-functions.md#cend)|检索一个指向指定容器中最后元素之后的元素的常量迭代器。|  
|[distance](../standard-library/iterator-functions.md#distance)|确定两个迭代器定址位置之间的增量数。|  
|[end](../standard-library/iterator-functions.md#end)|检索指向指定容器中最后一个元素之后的元素的迭代器。|  
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|创建一个可以在指定容器前面插入元素的迭代器。|  
|[inserter](../standard-library/iterator-functions.md#inserter)|一个可以在指定插入点向容器添加新元素的迭代器适配器。|  
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|创建可由其他算法使用的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。 **注意：**该函数是 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|  
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|返回一个移动迭代器，其中包含所提供的迭代器作为其存储的基迭代器。|  
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|创建可由其他算法使用的 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。 **注意：**该函数是 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|  
|[next](../standard-library/iterator-functions.md#next)|迭代指定的次数并返回新的迭代器位置。|  
|[prev](../standard-library/iterator-functions.md#prev)|反向迭代指定的次数并返回新的迭代器位置。|  
  
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
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|此模板类描述输出迭代器对象。 它可以将元素插入到 **Container** 类型的容器，并通过其存储的受保护 **pointer** 对象（称为容器）访问此容器。|  
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|一种为代表双向迭代器的 **iterator_category** 函数提供返回类型的类。|  
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|一种使用随机访问检查迭代器来访问数组的类。 **注意：**此类为 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|  
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|一种为代表向前迭代器的 **iterator_category** 函数提供返回类型的类。|  
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|此模板类描述输出迭代器对象。 它可以将元素插入到 **Container** 类型的容器，并通过其存储的受保护 **pointer** 对象（称为容器）访问此容器。|  
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|一种为代表输入迭代器的 **iterator_category** 函数提供返回类型的类。|  
|[insert_iterator](../standard-library/insert-iterator-class.md)|此模板类描述输出迭代器对象。 它可以将元素插入到 **Container** 类型的容器，并通过其存储的受保护 **pointer** 对象（称为容器）访问此容器。 它也可以存储受保护的 **iterator** 对象（**Container::iterator** 类），称为 **iter**。|  
|[istream_iterator](../standard-library/istream-iterator-class.md)|此模板类描述输入迭代器对象。 它可以从输入流中提取 **Ty** 类的对象，并通过其存储的、指向 `basic_istream`\<**Elem**, **Tr**> 的 pointer 类型对象进行访问。|  
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|此模板类描述输入迭代器对象。 它可以将 **Elem** 类对象插入到输出流缓冲区，并通过其存储的、指向 `basic_streambuf`\<**Elem**, **Tr**> 的 **pointer** 类型对象进行访问。|  
|[iterator](../standard-library/iterator-struct.md)|模板类用作所有迭代器的基类型。|  
|[iterator_traits](../standard-library/iterator-traits-struct.md)|一种模板 helper 类，可以提供与不同迭代器类型相关联的关键类型，以便用相同的方式引用这些迭代器。|  
|[move_iterator](../standard-library/move-iterator-class.md)|`move_iterator` 对象可以存储 `RandomIterator` 类型的随机访问迭代器。 它的行为类似于随机访问迭代器，但在解引用时除外。 `operator*` 的结果将隐式强制转换为 `value_type&&:`，以便形成 `rvalue reference`。|  
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|此模板类描述输出迭代器对象。 它可以将 **Type** 类对象插入到输出流，并通过其存储的、指向 `basic_ostream`\<**Elem**, **Tr**> 的 **pointer** 类型对象进行访问。|  
|[ostreambuf_iterator 类](../standard-library/ostreambuf-iterator-class.md)|此模板类描述输出迭代器对象。 它可以将 **Elem** 类对象插入到输出流缓冲区，并通过其存储的、指向 `basic_streambuf`\<**Elem**, **Tr**> 的 pointer 类型对象进行访问。|  
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|一种为代表输出迭代器的 **iterator_category** 函数提供返回类型的类。|  
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|一种为代表随机访问迭代器的 **iterator_category** 函数提供返回类型的类。|  
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|此模板类描述一个行为类似于随机访问迭代器的对象，只不过方向相反。|  
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|一种使用随机访问未检查迭代器来访问数组的类。 **注意：**此类为 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




