---
title: "简单变量声明 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
caps.latest.revision: 9
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 03d3939ef04a6a1a8bc5e3cd3ec5bfe56236ca0f
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="simple-variable-declarations"></a>简单变量声明
简单变量的声明（直接声明符的最简单形式）指定变量的名称和类型。 它还指定变量的存储类和数据类型。  
  
 变量声明需要存储类和/或类型。 非类型化变量（如 `var;`）会生成警告。  
  
## <a name="syntax"></a>语法  
 `declarator`：  
pointer ** opt  
  
 direct-declarator  
  
 *direct-declarator*：  
 *identifier*  
  
 identifier：  
nondigit **  
  
 identifier nondigit  
  
 identifier digit  
  
 对于算术、结构、联合、枚举和 void 类型以及由 `typedef` 名称表示的类型，可以在声明中使用简单声明符，因为类型说明符提供了所有类型化信息。 指针、数组和函数类型需要更复杂的声明符。  
  
 可以使用一系列由逗号 (,) 分隔的标识符来指定同一个声明中的多个变量。 声明中定义的所有变量都具有相同的基类型。 例如：  
  
```  
int x, y;        /* Declares two simple variables of type int */  
int const z = 1; /* Declares a constant value of type int */  
```  
  
 变量 `x` 和 `y` 可以保留由特定实现的 `int` 类型定义的集中的任何值。 简单对象 `z` 将初始化为值 1 且不可修改。  
  
 如果 `z` 的声明针对未初始化的静态变量或在文件范围内，则它将接收初始值 0，并且该值是不可修改的。  
  
```  
unsigned long reply, flag; /* Declares two variables  
                              named reply and flag     */  
```  
  
 在此示例中，两个变量（`reply` 和 `flag`）具有 `unsigned long` 类型并包含无符号的整数值。  
  
## <a name="see-also"></a>另请参阅  
 [声明符和变量声明](../c-language/declarators-and-variable-declarations.md)
