---
title: "算法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "算法模板函数 C++ 库约定"
  - "算法 [C++], C++"
  - "约定 [C++], C++ 算法"
  - "库 [C++], C++ 算法约定"
  - "标准 C++ 库, 算法"
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 算法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

算法是标准模板库的基础部分。  算法不与容器本身一起使用，而与迭代器一起使用。  因此，大多数（如果不是全部）STL 容器都可以使用相同的算法。  本部分讨论 STL 算法的约定和术语。  
  
## 备注  
 算法模板函数的说明使用几个速记短语：  
  
-   短语“in the range \[*A*, *B*\)”表示从 *A* 开始到 *B*（不包括 B）的零个或多个离散值的序列。  仅当可以从 *A* 到达 *B* 时，范围有效；可将 *A* 存储在对象 *N* \(*N* \= *A*\) 中，零次或多次增大该对象 \(\+\+*N*\)，以及使该对象在增大有限次数后等于 *B* \(N \=\= B*\)。*  
  
-   短语“each *N* in the range \[*A*, *B*\)”表示 *N* 以值 *A* 开始并增大零次或多次，直至等于值 *B*。  *N* \=\= *B* 的情况不在范围内。  
  
-   短语“the lowest value of *N* in the range \[*A*, *B*\) such that *X*”表示确定范围 \[*A*, *B*\) 中的每个 *N* 是否满足条件 *X*，直到满足条件 *X*。  
  
-   短语“the highest value of *N* in the range \[*A*, *B*\) such that *X*”表示确定范围 \[*A*, *B*\) 中的每个 *N* 是否满足 *X*。  每次满足条件 *X*，该函数即在 `K` 中存储 *N* 的一个副本。  如果发生此类存储，则该函数将最终值 *N*（等于 *B*）替换为值 `K`。  但是，对于双向或随机访问迭代器，这还意味着 *N* 从范围内的最高值开始在范围内减小，直到满足条件 *X*。  
  
-   表达式 *X* \- *Y*，其中 *X* 和 *Y* 可以是随机访问迭代器以外的迭代器，且应具有数学意义。  如果该函数必须确定此类值，则它不一定会评估 **operator\-**。  对于 *X* \+ *N* 和 *X* \- *N*（其中 *N* 是整数类型）等表达式也是如此。  
  
 几种算法使用进行成对比较的谓词（例如 `operator==`）生成 `bool` 结果。  谓词函数 `operator==` 或其任何替代函数不得更改其任一操作数。  每次计算都必须生成相同的 `bool` 结果，且当任一操作数的副本替换了操作数时，也必须生成相同的结果。  
  
 几种算法使用对序列中的元素对执行严格弱排序的谓词。  对于谓词 `pr`\(*X*, *Y*\)：  
  
-   严格意味着 `pr`\(*X*, *X*\) 为 false。  
  
-   弱意味着如果 \!`pr`\(*X*, *Y*\) && \!`pr`\(*Y*, *X*\)，则 *X* 和 *Y* 具有等效排序（无需定义 *X* \=\= *Y*）。  
  
-   排序意味着 `pr`\(*X*, *Y*\) \(& a\) \(& a\) `pr`\(*Y*, Z\) 表示 `pr`\(*X*, Z\)。  
  
 以上一些算法隐式使用谓词 *X* \< *Y*。  通常满足严格弱排序要求的其他谓词有 *X* \> *Y*、**less**\(*X*、*Y*\) 和 `greater`\(*X*, *Y*\)。  但请注意，*X* \<\= *Y* 和 *X* \>\= *Y* 等谓词不满足这一要求。  
  
 由迭代器在范围 \[`First`, `Last`\) 内指定的元素序列是由 **operator\<** 排序的序列，如果对于范围 \[0, `Last` \- `First`\) 中的每个 N 和范围 \(N, `Last` \- `First`\) 中的每个 M，谓词 \!\(\*\(`First` \+ *M*\) \< \*\(*First* \+ *N*\)\) 为 true。  （请注意元素以升序进行排序）。 谓词函数 **operator\<** 或任何其替代函数不得更改其任一操作数。  每次计算都必须生成相同的 `bool` 结果，且当任一操作数的副本替换了操作数时，也必须生成相同的结果。  此外，必须对它比较的操作数进行严格弱排序。  
  
 由迭代器在范围 \[`First`, `Last`\) 内指定的元素序列是由 **operator\<** 排序的堆，如果对于范围 \[1, `Last` \- `First`\)，谓词 \!\(\*`First` \< \*\(`First` \+ *N*\)\) 为 true。  （第一个元素最大。） 否则，其内部结构仅对模板函数 [make\_heap](../Topic/make_heap.md)、[pop\_heap](../Topic/pop_heap.md) 和 [push\_heap](../Topic/push_heap.md) 公开。  就有序序列来说，谓词函数 **operator\<**（或其任何替代函数）不得更改任一操作数，且必须对将它比较的操作数进行严格弱排序。  每次计算都必须生成相同的 `bool` 结果，且当任一操作数的副本替换了操作数时，也必须生成相同的结果。  
  
 STL 算法位于 [\<algorithm\>](../standard-library/algorithm.md) 和 [\<numeric\>](../standard-library/numeric.md) 头文件中。  
  
## 请参阅  
 [标准模板库](../misc/standard-template-library.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)