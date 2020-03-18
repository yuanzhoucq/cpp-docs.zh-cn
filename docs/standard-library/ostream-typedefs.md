---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425303"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

从 basic_ostream 创建一个类型，该类型在**char**上专用化并 `char_traits` 专用**化。**

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ostream](../standard-library/basic-ostream-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="wostream"></a>  wostream

从 basic_ostream 创建一个类型，该类型专用于**wchar_t**并 `char_traits` 专用于**wchar_t**。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ostream](../standard-library/basic-ostream-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="see-also"></a>另请参阅

[\<ostream>](../standard-library/ostream.md)
