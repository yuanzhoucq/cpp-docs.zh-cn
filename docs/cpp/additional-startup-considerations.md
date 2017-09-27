---
title: "附加启动注意事项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: cb437729d2c60f15bc798438ecbbba0637bf3d22
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="additional-startup-considerations"></a>附加启动注意事项
在 C++ 中，对象构造和析构可能涉及执行用户代码。 因此，务必了解在输入前发生的初始化**主要**退出后调用的析构函数和**主要**。 (有关构造和析构的对象的详细信息，请参阅[构造函数](../cpp/constructors-cpp.md)和[析构函数](../cpp/destructors-cpp.md)。)  
  
 在进入之前发生以下初始化**主要**:  
  
-   静态数据默认初始化为零。 没有显式初始值设定项的所有静态数据在执行任何其他代码（包括运行时初始化）前设置为零。 静态数据成员仍必须显式定义。  
  
-   翻译单元中的全局静态对象的初始化。 这可能是之前进入或是**主要**或之前的任何函数或对象的翻译单元中的对象的第一种用法。  
  
 **Microsoft 专用**  
  
 Microsoft c + + 中的全局静态对象之前，将初始化进入**主要**。  
  
 **结束 Microsoft 专用**  
  
 相互依赖但位于不同翻译单元中的全局静态对象会导致错误行为。  
  
## <a name="see-also"></a>另请参阅  
 [启动和终止](../cpp/startup-and-termination-cpp.md)
