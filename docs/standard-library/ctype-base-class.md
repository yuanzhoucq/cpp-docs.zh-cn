---
title: "ctype_base 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::ctype_base
- ctype_base
dev_langs:
- C++
helpviewer_keywords:
- ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: 19
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 74c13251b63018e00490487cb9a45c4bb6d52a21
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="ctypebase-class"></a>ctype_base 类
该类用作模板类 [ctype](../standard-library/ctype-class.md) 的 facet 基类。 一种 ctype 类的基类，用于定义枚举类型来分类或测试单个字符或整个范围内的字符。  
  
## <a name="syntax"></a>语法  
  
```
struct ctype_base : public locale::facet
{
    enum
 {
    alnum,
 alpha,
    cntrl,
 digit,
    graph,
 lower,
    print,
 punct,
    space,
 upper,
    xdigit
 };
    typedef short mask;
    ctype_base(
 size_t _Refs = 0);

 ~ctype_base();

};
```  
  
## <a name="remarks"></a>备注  
 它定义了枚举掩码。 每个枚举常量都表现为一种不同方式来对字符进行分类，正如在标头 \<ctype.h 1> 中声明的具有类似名称的函数所定义。 这些常量包括：  
  
- **space**（函数 [isspace](../standard-library/locale-functions.md#isspace)）  
  
- **print**（函数 [isprint](../standard-library/locale-functions.md#isprint)）  
  
- **cntrl**（函数 [iscntrl](../standard-library/locale-functions.md#iscntrl)）  
  
- **upper**（函数 [isupper](../standard-library/locale-functions.md#isupper)）  
  
- **lower**（函数 [islower](../standard-library/locale-functions.md#islower)）  
  
- **digit**（函数 [isdigit](../standard-library/locale-functions.md#isdigit)）  
  
- **punct**（函数 [ispunct](../standard-library/locale-functions.md#ispunct)）  
  
- **xdigit**（函数 [isxdigit](../standard-library/locale-functions.md#isxdigit)）  
  
- **alpha**（函数 [isalpha](../standard-library/locale-functions.md#isalpha)）  
  
- **alnum**（函数 [isalnum](../standard-library/locale-functions.md#isalnum)）  
  
- **graph**（函数 [isgraph](../standard-library/locale-functions.md#isgraph)）  
  
 通过实现或运算这些常量，可以确定分类组合的特征。 具体来说，**alnum** == ( **alpha**``&#124; **digit**\) and **graph** \=\= \( **alnum**``&#124; **punct**) 始终为 true。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




