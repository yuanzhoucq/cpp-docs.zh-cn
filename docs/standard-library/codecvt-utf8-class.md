---
title: codecvt_utf8
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf8
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
ms.openlocfilehash: dcbb34c300d7c15f89c4a882275be0efd68359dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458716"
---
# <a name="codecvtutf8"></a>codecvt_utf8

表示在编码为 UCS-2 或 UCS-4 的宽字符和编码为 UTF-8 的字节流之间转换的 [locale](../standard-library/locale-class.md) facet。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>参数

*Elem*\
宽字符元素类型。

*Maxcode*\
区域设置 facet 的最大字符数。

*众*\
配置区域设置 facet 的信息。

## <a name="remarks"></a>备注

字节流可以写入二进制文件或文本文件。

## <a name="requirements"></a>要求

标头\<: codecvt >

命名空间: std
