---
title: "auto 关键字 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: auto_cpp
dev_langs: C++
helpviewer_keywords:
- automatic storage class [C++], auto keyword
- auto keyword [C++]
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3508217e7dc333543fa2dbff9cf0643d6faff060
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)