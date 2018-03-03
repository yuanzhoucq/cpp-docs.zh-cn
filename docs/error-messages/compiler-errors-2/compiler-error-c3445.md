---
title: "编译器错误 C3445 |Microsoft 文档"
ms.custom: 
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf0ba819aa1e8f0a7651e7c42e457b5766c9eefd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3445"></a>编译器错误 C3445
复制列表的初始化的*类型*不能使用的显式构造函数  
  
根据 ISO C + + 17 标准中，编译器需要考虑在副本列表初始化的重载决策的显式构造函数，但如果实际选择该重载，则必须引发错误。  
  
从 Visual Studio 2017 年 1 开始，编译器找不使用初始值设定项列表与对象创建相关的错误，未找到由 Visual Studio 2015。 这些错误可能导致发生崩溃或未定义在运行时的行为。

## <a name="example"></a>示例  
 下面的示例生成 C3445。  
  
```cpp  
// C3445.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of 
                      //     'A' cannot use an explicit constructor
}
```  
  
若要更正错误，请改为使用直接初始化：  
  
```cpp  
// C3445b.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1{ 1 };
}  
```  
  