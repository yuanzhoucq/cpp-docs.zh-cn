---
title: "char_traits&lt;char&gt; 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
dev_langs: C++
helpviewer_keywords: char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbccd8b7a37f051fc9ef7d8e42b6d86f49a9c1b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
