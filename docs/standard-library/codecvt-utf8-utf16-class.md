---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 42c9c8643edc795748c1f12c5180471f281c4142
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630667"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

表示在编码为 UTF-16 的宽字符和编码为 UTF-8 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

*Elem*<br/>
宽字符元素类型。

*Maxcode*<br/>
区域设置 facet 的最大字符数。

*模式*<br/>
配置区域设置 facet 的信息。

## <a name="remarks"></a>备注

字节流可以写入二进制文件或文本文件。

## <a name="requirements"></a>要求

标头： \<codecvt >

Namespace: std
