---
title: "迭代器 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f03b62e045fe0130f981d55767c756df89bca9c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iterators"></a>Iterators
迭代器是一个对象，可以循环访问 C++ 标准库容器中的元素，并提供对各个元素的访问。 C++ 标准库容器全都提供迭代器，以便算法可以采用标准方式访问其元素，而不必考虑用于存储元素的容器类型。  
  
 可以通过使用成员和全局函数（如 begin() 和 end()）以及运算符（如 ++ 和 -- ）向前或向后移动，来显式使用迭代器。 还可以通过范围 for 循环或（对于某些迭代器类型）下标运算符 []，来隐式使用迭代器。  
  
 在 C++ 标准库中，序列或范围的开头是第一个元素。 序列或范围的末尾始终定义为最后一个元素的下一个位置。 全局函数的开始和结束会将迭代器返回到指定容器。 典型显式迭代器循环访问容器中的所有元素，如下所示：  
  
```  
 
vector<int> vec{ 0,1,2,3,4 };  
for (auto it = begin(vec);

it != end(vec);

it++)  
{  // Access element using dereference operator
    cout <<*it <<" ";  
}  
```  
  
 可以使用范围 for 循环更加简单地完成相同操作：  
  
```  
for (auto num : vec)  
 {  // no deference operator
    cout <<num <<" ";  
 }  
```  
  
 有五种类别的迭代器。 这些类别如下所示（按功能逐渐增强的顺序）：  
  
- **输出**。 输出迭代器 `X` 可以使用 ++ 运算符向前循环访问序列，并且可以使用 * 运算符将元素仅写入一次。  
  
- **输入**。 输入迭代器 `X` 可以使用 ++ 运算符向前循环访问序列，并且可以使用 * 运算符读取元素任意次数。 可以使用 ++ 和 != 运算符比较输入迭代器。 递增输入迭代器的任何副本之后，没有其他任何副本可以安全地进行比较、取消引用或递增。  
  
- **向前**。 向前迭代器 `X` 可以使用 ++ 运算符向前循环访问序列，并且可以使用 * 运算符读取任意元素或写入非常量元素任意次数。 可以使用 -> 运算符访问元素成员，并使用 == 和 != 运算符比较向前迭代器。 可以创建向前迭代器的多个副本，其中每个副本都可以独立地取消引用和递增。 未使用对任何容器的引用进行初始化的向前迭代器称为 null 向前迭代器。 Null 向前迭代器的比较结果始终是相等的。  
  
-   双向。 双向迭代器 `X` 可以替代向前迭代器。 但是，还可以递减双向迭代器，如 --`X`、`X`-- 或 (`V` = *`X`--)。 可以采用与向前迭代器相同的方式访问元素成员和比较双向迭代器。  
  
- **随机访问**。 随即访问迭代器 `X` 可以替代双向迭代器。 借助随机访问迭代器，可以使用下标运算符 [] 访问元素。 可以使用 +、-、+= 和 -= 运算符向前或向后移动指定数量的元素以及计算迭代器之间的距离。 可以使用 ==、!=、\<、>、\<= 和 >= 比较双向迭代器。  
  
 可以分配或复制所有迭代器。 它们被假定为轻量对象，通常按值（而不是按引用）进行传递和返回。 另请注意，前面所述的操作都无法在对有效迭代器执行时引发异常。  
  
 可以通过显示三个序列来汇总迭代器类别的层次结构。 若要对序列进行只写访问，可以使用以下任何项：  
  
```  
output iterator  
 -> forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 向右箭头标识“可以替代”。 例如，为输出迭代器调用的任何算法都应十分适用于向前迭代器，而不是相反。  
  
 若要对序列进行只读访问，可以使用以下任何项：  
  
```  
input iterator  
 -> forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 输入迭代器在这种情况下是所有类别中最弱的。  
  
 最后，若要对序列进行读/写访问，可以使用以下任何项：  
  
```  
forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 对象指针可以始终充当随机访问迭代器，因此如果它支持对它指定的序列进行正确的读/写访问，则它可以充当任何类别的迭代器。  
  
 对象指针以外的迭代器 `Iterator` 还必须定义专用化 `iterator_traits<Iterator>` 所需的成员类型。 请注意，可以通过从公共基类 [iterator](../standard-library/iterator-struct.md) 派生 `Iterator` 来满足这些需求。  
  
 请务必了解每个迭代器类别的承诺和限制，以便了解 C++ 标准库中的容器和算法如何使用迭代器。  
  
> [!NOTE]
>  可以使用范围 for 循环来避免显式使用迭代器。 有关详细信息，请参阅[循环（现代 C++）](http://msdn.microsoft.com/en-us/b1b2779c-750e-4576-a514-a84178eae9da)。  
  
 Visual c + + 现在提供了检查迭代器和调试迭代器，以确保不会覆盖你的容器的界限。 有关详细信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)和[调试迭代器支持](../standard-library/debug-iterator-support.md)。  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

