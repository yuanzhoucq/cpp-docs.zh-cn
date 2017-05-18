---
title: "char_traits&lt;char&gt; 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- string/std::char_traits<char>
- char_traits<char >
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
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
ms.openlocfilehash: 0cf4c829018016f255ceab407f905fd15114c7f4
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt; 结构
此结构是模板结构 **char_traits\<CharType>** 对 `char` 类型的一个元素的专用化。  
  
## <a name="syntax"></a>语法  
  
```
template <>  
struct char_traits<char>;
```  
  
## <a name="remarks"></a>备注  
 专用化允许结构利用库函数处理此 `char` 类型的对象。  
  
## <a name="example"></a>示例  
 查看模板类 [char_traits 类](../standard-library/char-traits-struct.md) 的 typedef 和成员函数

