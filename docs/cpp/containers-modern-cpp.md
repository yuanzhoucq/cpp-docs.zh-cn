---
title: "容器 （现代 c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ffad61c015c38d808b35ebffd98f74733d0997de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="containers-modern-c"></a>容器（现代 C++）  
  
默认情况下，使用[向量](../standard-library/vector-class.md)作为 c + + 中的首选顺序容器。 这相当于`List<T>`.NET 语言。  
  
```cpp  
vector<string> apples;  
apples.push_back("Granny Smith");  
```  
  
使用[映射](../standard-library/map-class.md)(不`unordered_map`) 作为默认关联容器。 使用[设置](../standard-library/set-class.md)，[多重映射](../standard-library/multimap-class.md)，和[多重集](../standard-library/multiset-class.md)退化和多用例。  
  
```cpp  
map<string, string> apple_color;  
// ...  
apple_color["Granny Smith"] = "Green";  
```  
  
当需要性能优化时，请考虑使用：  
  
1.  [数组](../standard-library/array-class-stl.md)键入嵌入十分重要，例如，作为类成员时。  
  
2.  无序 [unordered_map] 等的关联容器 ((.../standard-library/unordered-map-class.md)。 这些开销具有较低的每个元素，并且常量时间查找，但它们可以作为难以正确有效地使用。  
  
3.  排序`vector`。 有关详细信息，请参阅[算法](../cpp/algorithms-modern-cpp.md)。  
  
不要使用 C 样式数组。 对于需要直接访问数据的较旧 Api，使用访问器方法如`f(vec.data(), vec.size());`相反。  
  
有关容器的详细信息，请参阅[c + + 标准库容器](../standard-library/stl-containers.md)。  
  
## <a name="see-also"></a>请参阅  
 [欢迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)
