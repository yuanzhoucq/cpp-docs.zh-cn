---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 18f30a12a6f4d2b97cb5dca3ace98e6241d856a7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447168"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

从 basic_ostream 中创建专用于**char**的类型并`char_traits`在**char**上专用化。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_ostream](../standard-library/basic-ostream-class.md)的同义词, 专用于具有默认字符特征的**char**类型的元素。

## <a name="wostream"></a>  wostream

从 basic_ostream 创建一个类型, 该类型专用于 wchar_t `char_traits`并专用于**wchar_t**。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_ostream](../standard-library/basic-ostream-class.md)的同义词, 专用于具有默认字符特征的**wchar_t**类型的元素。

## <a name="see-also"></a>请参阅

[\<ostream>](../standard-library/ostream.md)
