---
title: "checked_array_iterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/checked_array_iterator"
  - "checked_array_iterator"
  - "std::checked_array_iterator"
  - "std.checked_array_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "checked_array_iterator"
  - "checked_array_iterator 类"
  - "checked_array_iterator, 语法"
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# checked_array_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过 `checked_array_iterator` 类，可以将数组或指针转换为经检查的迭代器。  使用此类作为原始指针或数组的包装器（使用 [make\_checked\_array\_iterator](../Topic/make_checked_array_iterator.md) 函数）可以有针对性地提供检查并管理未经检查的指针警告，无需从全局静默处理这些警告。  如有必要，可以使用此类的未经检查版本 [unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)。  
  
> [!NOTE]
>  此类为标准 C\+\+ 库的 Microsoft 扩展。  使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C\+\+ 标准生成环境中。  有关演示如何编写无需使用此类的代码的示例，请参阅下面第二个示例。  
  
## 语法  
  
```  
template <class _Iterator>  
    class checked_array_iterator;  
```  
  
## 备注  
 此类在 [stdext](../standard-library/stdext-namespace.md) 命名空间中定义。  
  
 有关经检查迭代器功能的详细信息和代码示例，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
## 示例  
 下面的示例演示如何定义和使用经检查的数组迭代器。  
  
 如果目标不够大，无法保留复制的所有元素，例如你将行：  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
```  
  
 比较目标  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 4));  
```  
  
 将发生运行时错误。  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[]={0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
  
   // constructor example  
   checked_array_iterator<int*> checked_out_iter(b, 5);  
   copy(a, a + 5, checked_out_iter);  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
}  
```  
  
  **\( 0 1 2 3 4 \)**  
**\( 0 1 2 3 4 \)**   
## 示例  
 若要在使用标准 C\+\+ 库算法时避免使用 `checked_array_iterator` 类，请考虑使用 `vector` 而不是动态分配的数组。  下面的示例演示如何执行此操作。  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
  
#include <algorithm>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
    std::vector<int> v(10);  
    int *arr = new int[10];  
    for (int i = 0; i < 10; ++i)  
    {  
        v[i] = i;  
        arr[i] = i;  
    }  
  
    // std::copy(v.begin(), v.end(), arr); will result in  
    // warning C4996. To avoid this warning while using int *,  
    // use the Microsoft extension checked_array_iterator.  
    std::copy(v.begin(), v.end(),  
              stdext::checked_array_iterator<int *>(arr, 10));  
  
    // Instead of using stdext::checked_array_iterator and int *,  
    // consider using std::vector to encapsulate the array. This will  
    // result in no warnings, and the code will be portable.  
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];  
    std::copy(v.begin(), v.end(), arr2.begin());  
  
    for (int j = 0; j < arr2.size(); ++j)  
    {  
        cout << " " << arr2[j];  
    }  
    cout << endl;  
  
    return 0;  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**   
### 构造函数  
  
|||  
|-|-|  
|[checked\_array\_iterator](../Topic/checked_array_iterator::checked_array_iterator.md)|构造默认 `checked_array_iterator` 或从基础迭代器构造 `checked_array_iterator`。|  
  
### Typedef  
  
|||  
|-|-|  
|[difference\_type](../Topic/checked_array_iterator::difference_type.md)|一种类型，此类型提供引用同一容器中的元素的两个 `checked_array_iterator` 之间的差异。|  
|[指针](../Topic/checked_array_iterator::pointer.md)|一种类型，此类型提供指向 `checked_array_iterator` 所发现元素的指针。|  
|[引用](../Topic/checked_array_iterator::reference.md)|一种类型，此类型提供对 `checked_array_iterator` 所发现元素的引用。|  
  
### 成员函数  
  
|||  
|-|-|  
|[基项](../Topic/checked_array_iterator::base.md)|将基础迭代器从其 `checked_array_iterator` 恢复。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\=\=](../Topic/checked_array_iterator::operator==.md)|测试两个 `checked_array_iterator` 是否相等。|  
|[operator\!\=](../Topic/checked_array_iterator::operator!=.md)|测试两个 `checked_array_iterator` 是否不相等。|  
|[运算符 \<](../Topic/checked_array_iterator::operator%3C.md)|测试运算符左侧的 `checked_array_iterator` 是否小于右侧的 `checked_array_iterator`。|  
|[运算符 \>](../Topic/checked_array_iterator::operator%3E.md)|测试运算符左侧的 `checked_array_iterator` 是否大于右侧的 `checked_array_iterator`。|  
|[运算符 \<\=](../Topic/checked_array_iterator::operator%3C=.md)|测试运算符左侧的 `checked_array_iterator` 是否小于或等于右侧的 `checked_array_iterator`。|  
|[运算符 \>\=](../Topic/checked_array_iterator::operator%3E=.md)|测试运算符左侧的 `checked_array_iterator` 是否大于或等于右侧的 `checked_array_iterator`。|  
|[operator\*](../Topic/checked_array_iterator::operator*.md)|返回 `checked_array_iterator` 发现的元素。|  
|[operator\-\>](../Topic/checked_array_iterator::operator-%3E.md)|返回指向 `checked_array_iterator` 发现的元素的指针。|  
|[operator\+\+](../Topic/checked_array_iterator::operator++.md)|将 `checked_array_iterator` 递增到下一元素。|  
|[operator\-\-](../Topic/checked_array_iterator::operator--.md)|将 `checked_array_iterator` 递减到前一元素。|  
|[运算符 \+\=](../Topic/checked_array_iterator::operator+=.md)|将指定偏移量添加到 `checked_array_iterator`。|  
|[运算符 \+](../Topic/checked_array_iterator::operator+.md)|将偏移量添加到迭代器，并返回在新偏移位置处发现插入元素的新 `checked_array_iterator`。|  
|[operator\-\=](../Topic/checked_array_iterator::operator-=.md)|从 `checked_array_iterator` 递减指定偏移量。|  
|[operator\-](../Topic/checked_array_iterator::operator-.md)|从迭代器递减偏移量，并返回在新偏移位置处发现插入元素的新 `checked_array_iterator`。|  
|[operator&#91;&#93;](../Topic/checked_array_iterator::operator.md)|返回对于从 `checked_array_iterator` 发现的元素偏移指定个位置的元素的引用。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [标准模板库](../misc/standard-template-library.md)