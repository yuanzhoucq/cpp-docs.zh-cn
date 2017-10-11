---
title: "codecvt_utf16 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 68b6b058d6962758a3b3e42fcde943699820fa12
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="codecvtutf16"></a>codecvt_utf16
表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 或 UTF-16BE 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```
## <a name="parameters"></a>参数
`Elem`  
宽字符元素类型。  
`Maxcode`  
区域设置 facet 的最大字符数。  
`Mode`  
配置区域设置 facet 的信息。  

## <a name="remarks"></a>备注
此模板类在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 的字节流之间转换，编码为 Mode 和 little_endian 或 UTF-16BE 则除外。

字节流应写入二进制文件；如果写入文本文件，则可能会损坏。

## <a name="requirements"></a>要求
标头：\<codecvt> Namespace: std
