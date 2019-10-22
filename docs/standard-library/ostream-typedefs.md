---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687233"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

从 basic_ostream 中创建专用于**char**的类型，并 `char_traits` 专用于**char**。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ostream](../standard-library/basic-ostream-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="wostream"></a>  wostream

从 basic_ostream 中创建专用于**wchar_t**的类型，并在**wchar_t**上专门 `char_traits`。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ostream](../standard-library/basic-ostream-class.md)的同义词，专用于具有默认字符特征的**wchar_t**类型的元素。

## <a name="see-also"></a>请参阅

[\<ostream>](../standard-library/ostream.md)
