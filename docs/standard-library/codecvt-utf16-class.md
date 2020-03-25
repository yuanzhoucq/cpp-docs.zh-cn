---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 73177985727f4da5cf3ca4eb9e3cc3fb5976f76d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215275"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 或 UTF-16BE 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>parameters

*Elem*\
宽字符元素类型。

*Maxcode*\
区域设置 facet 的最大字符数。

*模式*\
配置区域设置 facet 的信息。

## <a name="remarks"></a>备注

此类模板在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 的字节流之间进行转换，如果模式 & little_endian 或 UTF-16BE，则为; 否则为。

字节流应写入二进制文件；如果写入文本文件，则可能会损坏。

## <a name="requirements"></a>要求

标头： \<codecvt >

命名空间: std
