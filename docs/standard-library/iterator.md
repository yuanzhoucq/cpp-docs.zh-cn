---
title: "&lt;iterator&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::<iterator>"
  - "std.<iterator>"
  - "<iterator>"
  - "iterator/std::<iterator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator 标头"
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# &lt;iterator&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义迭代器基元、预定义的迭代器和流迭代器，以及一些支持模板。  预定义的迭代器包含插入及反向适配器。  插入迭代器适配器包括三类：前向、后向和常规。  它们提供的是插入语义而不是容器成员函数迭代器所提供的覆盖语义。  
  
## 语法  
  
```  
  
#include <iterator>  
  
```  
  
## 备注  
 迭代器是指针的泛化，它从这些指针的要求中抽象出来，允许 C\+\+ 程序使用统一的方式来处理不同的数据结构。  迭代器充当容器和泛型算法之间的媒介。  算法被定义为对某一迭代器类型所指定的范围起作用，而不是作用于特定的数据类型。  随后，算法可能会作用于任何满足迭代器要求的数据结构。  迭代器有五个类型或类别，各自具有自己的要求和最终功能：  
  
-   输出：向前移动，可以存储但不能检索值，由 ostream 和 inserter 提供。  
  
-   输入：向前移动，可以检索但不能存储值，由 istream 提供。  
  
-   向前：向前移动，可以存储和检索值。  
  
-   双向：向前和向后移动，可以存储和检索值，由列表、集合、多重集、映射和多重映射提供。  
  
-   随机访问：以任意顺序访问元素，可以存储和检索值，由向量、双端队列、字符串和数组提供。  
  
 可使用要求较高、因而需要更强大元素访问的迭代器来代替要求较低的迭代器。  例如，如果调用向前迭代器，则可使用随机访问迭代器来代替。  
  
 Visual Studio 为 C\+\+ 标准库迭代器增加了一些扩展，以便支持多种检查迭代器和未检查迭代器的调试模式情形。  有关详细信息，请参阅[安全库：C\+\+ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)。  
  
### 函数  
  
|||  
|-|-|  
|[advance](../Topic/advance.md)|使迭代器递增指定数量的位置。|  
|[back\_inserter](../Topic/back_inserter.md)|创建一个可以在指定容器的后面插入元素的迭代器。|  
|[begin](../Topic/begin.md)|检索一个指向指定容器中第一个元素的迭代器。|  
|[cbegin](../Topic/cbegin.md)|检索一个指向指定容器中第一个元素的常量迭代器。|  
|[cend](../Topic/cend.md)|检索一个指向指定容器中最后元素之后的元素的常量迭代器。|  
|[distance](../Topic/distance.md)|确定两个迭代器定址位置之间的增量数。|  
|[end](../Topic/end.md)|检索指向指定容器中最后一个元素之后的元素的迭代器。|  
|[front\_inserter](../Topic/front_inserter.md)|创建一个可以在指定容器前面插入元素的迭代器。|  
|[inserter](../Topic/inserter.md)|一个可以在指定插入点向容器添加新元素的迭代器适配器。|  
|[make\_checked\_array\_iterator](../Topic/make_checked_array_iterator.md)|创建可由其他算法使用的 [checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)。 **Note:**  该函数是标准 C\+\+ 库的 Microsoft 扩展。  使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C\+\+ 标准生成环境中。|  
|[make\_move\_iterator](../Topic/make_move_iterator.md)|返回一个移动迭代器，其中包含所提供的迭代器作为其存储的基迭代器。|  
|[make\_unchecked\_array\_iterator](../Topic/make_unchecked_array_iterator.md)|创建可由其他算法使用的 [unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)。 **Note:**  该函数是标准 C\+\+ 库的 Microsoft 扩展。  使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C\+\+ 标准生成环境中。|  
|[next](../Topic/next.md)|迭代指定的次数并返回新的迭代器位置。|  
|[prev](../Topic/prev.md)|反向迭代指定的次数并返回新的迭代器位置。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Citerator%3E\).md)|测试运算符左侧的迭代器对象是否不等于右侧的迭代器对象。|  
|[operator\=\=](../Topic/operator==%20\(%3Citerator%3E\).md)|测试运算符左侧的迭代器对象是否等于右侧的迭代器对象。|  
|[operator\<](../Topic/operator%3C%20\(%3Citerator%3E\).md)|测试运算符左侧的迭代器对象是否小于右侧的迭代器对象。|  
|[operator\<\=](../Topic/operator%3C=%20\(%3Citerator%3E\).md)|测试运算符左侧的迭代器对象是否小于或等于右侧的迭代器对象。|  
|[operator\>](../Topic/operator%3E%20\(%3Citerator%3E\).md)|测试运算符左侧的迭代器对象是否大于右侧的迭代器对象。|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Citerator%3E\).md)|测试运算符左侧的迭代器对象是否大于或等于右侧的迭代器对象。|  
|[operator\+](../Topic/operator+%20\(%3Citerator%3E\).md)|将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `reverse_iterator`。|  
|[operator\-](../Topic/operator-%20\(%3Citerator%3E\).md)|从另一个迭代器中减去一个迭代器并返回差值。|  
  
### 类  
  
|||  
|-|-|  
|[back\_insert\_iterator](../standard-library/back-insert-iterator-class.md)|此模板类描述输出迭代器对象。  它可以将元素插入到 **Container** 类型的容器，并通过其存储的受保护 **pointer** 对象（称为容器）访问此容器。|  
|[bidirectional\_iterator\_tag](../standard-library/bidirectional-iterator-tag-struct.md)|一种为代表双向迭代器的 **iterator\_category** 函数提供返回类型的类。|  
|[checked\_array\_iterator](../standard-library/checked-array-iterator-class.md)|一种使用随机访问检查迭代器来访问数组的类。 **Note:**  此类为标准 C\+\+ 库的 Microsoft 扩展。  使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C\+\+ 标准生成环境中。|  
|[forward\_iterator\_tag](../standard-library/forward-iterator-tag-struct.md)|一种为代表向前迭代器的 **iterator\_category** 函数提供返回类型的类。|  
|[front\_insert\_iterator](../standard-library/front-insert-iterator-class.md)|此模板类描述输出迭代器对象。  它可以将元素插入到 **Container** 类型的容器，并通过其存储的受保护 **pointer** 对象（称为容器）访问此容器。|  
|[input\_iterator\_tag](../standard-library/input-iterator-tag-struct.md)|一种为代表输入迭代器的 **iterator\_category** 函数提供返回类型的类。|  
|[insert\_iterator](../standard-library/insert-iterator-class.md)|此模板类描述输出迭代器对象。  它可以将元素插入到 **Container** 类型的容器，并通过其存储的受保护 **pointer** 对象（称为容器）访问此容器。  它也可以存储受保护的 **iterator** 对象（**Container::iterator** 类），称为 **iter**。|  
|[istream\_iterator](../standard-library/istream-iterator-class.md)|此模板类描述输入迭代器对象。  它可以从输入流中提取 **Ty** 类的对象，并通过其存储的、指向 `basic_istream`\<**Elem**, **Tr**\> 的 pointer 类型对象进行访问。|  
|[istreambuf\_iterator](../standard-library/istreambuf-iterator-class.md)|此模板类描述输入迭代器对象。  它可以将 **Elem** 类对象插入到输出流缓冲区，并通过其存储的、指向 `basic_streambuf`\<**Elem**, **Tr**\> 的 **pointer** 类型对象进行访问。|  
|[iterator](../standard-library/iterator-struct.md)|模板类用作所有迭代器的基类型。|  
|[iterator\_traits](../standard-library/iterator-traits-struct.md)|一种模板 helper 类，可以提供与不同迭代器类型相关联的关键类型，以便用相同的方式引用这些迭代器。|  
|[move\_iterator](../standard-library/move-iterator-class.md)|`move_iterator` 对象可以存储 `RandomIterator` 类型的随机访问迭代器。  它的行为类似于随机访问迭代器，但在解引用时除外。  `operator*` 的结果将隐式强制转换为 `value_type&&:`，以便形成 `rvalue reference`。|  
|[ostream\_iterator](../standard-library/ostream-iterator-class.md)|此模板类描述输出迭代器对象。  它可以将 **Type** 类对象插入到输出流，并通过其存储的、指向 `basic_ostream`\<**Elem**, **Tr**\> 的 **pointer** 类型对象进行访问。|  
|[ostreambuf\_iterator 类](../standard-library/ostreambuf-iterator-class.md)|此模板类描述输出迭代器对象。  它可以将 **Elem** 类对象插入到输出流缓冲区，并通过其存储的、指向 `basic_streambuf`\<**Elem**, **Tr**\> 的 pointer 类型对象进行访问。|  
|[output\_iterator\_tag](../standard-library/output-iterator-tag-struct.md)|一种为代表输出迭代器的 **iterator\_category** 函数提供返回类型的类。|  
|[random\_access\_iterator\_tag](../standard-library/random-access-iterator-tag-struct.md)|一种为代表随机访问迭代器的 **iterator\_category** 函数提供返回类型的类。|  
|[reverse\_iterator](../standard-library/reverse-iterator-class.md)|此模板类描述一个行为类似于随机访问迭代器的对象，只不过方向相反。|  
|[unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)|一种使用随机访问未检查迭代器来访问数组的类。 **Note:**  此类为标准 C\+\+ 库的 Microsoft 扩展。  使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C\+\+ 标准生成环境中。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)