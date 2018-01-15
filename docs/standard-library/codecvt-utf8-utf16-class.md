---
title: "codecvt_utf8_utf16 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: codecvt/std::cvt_utf8_utf16
dev_langs: C++
helpviewer_keywords: codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d16a5e316119470f96c115c4ba8cbe47fabd3831
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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

## <a name="requirements"></a>惠?

标头：<codecvt> Namespace: std
