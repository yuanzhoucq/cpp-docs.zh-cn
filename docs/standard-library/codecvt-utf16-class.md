---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 18b95884bb673305398739968ef2530e8c4778d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649132"
---
# <a name="codecvtutf16"></a>codecvt_utf16

表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 或 UTF-16BE 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

*Elem*<br/>
宽字符元素类型。

*Maxcode*<br/>
区域设置 facet 的最大字符数。

*模式*<br/>
配置区域设置 facet 的信息。

## <a name="remarks"></a>备注

此模板类在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-16LE 的字节流之间转换，编码为 Mode 和 little_endian 或 UTF-16BE 则除外。

字节流应写入二进制文件；如果写入文本文件，则可能会损坏。

## <a name="requirements"></a>要求

标头： \<codecvt >

Namespace: std