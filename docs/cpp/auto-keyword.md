---
title: "auto 关键字 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- auto_cpp
dev_langs:
- C++
helpviewer_keywords:
- automatic storage class [C++], auto keyword
- auto keyword [C++]
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0413fd47b486cf1613b7c249b93e6a3507a5577c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="auto-keyword"></a>auto 关键字
`auto` 关键字是声明说明符。 但是，C++ 标准为此关键字定义了初始和修订的含义。 Visual c + + 2010 之前,`auto`关键字声明中的变量*自动*存储类; 即，具有本地生存期的变量。 从 Visual c + + 2010，开始`auto`关键字声明从其声明中的初始化表达式中推导其类型的变量。 [/Zc: auto &#91;-&#93;](../build/reference/zc-auto-deduce-variable-type.md)编译器选项控制的含义`auto`关键字。  
  
## <a name="syntax"></a>语法  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>备注  
 `auto` 关键字的定义在 C++ 编程语言中更改，但在 C 编程语言中未更改。  
  
 下列主题描述 `auto` 关键字和对应的编译器选项：  
  
-   [自动](../cpp/auto-cpp.md)介绍的新定义`auto`关键字。  
  
  
-   [/Zc: auto （推导变量类型）](../build/reference/zc-auto-deduce-variable-type.md)描述告知编译器的哪些定义编译器选项`auto`关键字来使用。  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)
