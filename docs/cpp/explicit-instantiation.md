---
title: "显式实例化 |Microsoft 文档"
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
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ecd8f8c893abab10699a0bd43f368356335c6e10
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="explicit-instantiation"></a>显式实例化
你可以使用显式实例化来创建模板化类或函数的实例化，而不用将其实际用于你的代码。 创建库 (.lib) 文件，使用的模板分发时，这很有用，因为未实例化的模板定义未放入对象 (.obj) 文件。  
  
 此代码针对 `MyStack` 变量和六个项显式实例化 `int`：  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 该语句创建 `MyStack` 的实例化，而不保留对象的任何存储。 为所有成员生成代码。  
  
 下一行仅显式实例化构造函数成员函数：  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 你可以显式使用实例化函数模板的特定类型参数来重新声明这些中的示例中所示[函数模板实例化](../cpp/function-template-instantiation.md)。  
  
 你可以使用`extern`关键字以防止自动实例化的成员。 例如：  
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 同样，您可以将特定成员标记为外部且未实例化：  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 您可以使用 `extern` 关键字阻止编译器在多个对象模块中生成相同的实例化代码。 如果调用该函数，则必须在至少一个链接的模块中使用指定的显式模板参数来实例化模板函数，否则会在生成程序时收到链接器错误。  
  
> [!NOTE]
>  `extern`专用化中的关键字仅适用于类主体外部定义的成员函数。 类声明中定义的函数被视为内联函数，并且始终实例化。  
  
## <a name="see-also"></a>另请参阅  
 [函数模板](../cpp/function-templates.md)
