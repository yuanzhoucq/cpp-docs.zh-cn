---
title: "char_traits&lt;char&gt; 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6ba6aff287787b898744a0dabb25be21e4e96e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
