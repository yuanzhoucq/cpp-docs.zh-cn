---
title: "codecvt_utf8_utf16 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt_utf8_utf16
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: e628eb145b52cd3ab9b1e36770363c34099c6cb4
ms.lasthandoff: 02/24/2017

---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16
表示在编码为 UTF-16 的宽字符和编码为 UTF-8 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

`Elem`  
宽字符元素类型。  
`Maxcode`  
区域设置 facet 的最大字符数。  
`Mode`  
配置区域设置 facet 的信息。  

## <a name="remarks"></a>备注

字节流可以写入二进制文件或文本文件。  

## <a name="requirements"></a>要求

标头：<codecvt> Namespace: std

