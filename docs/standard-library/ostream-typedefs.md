---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 02936fdfc990ea65a99b2875cf7f482eb2ce4ebe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429739"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

创建类型上专用化的 basic_ostream **char**并`char_traits`专用于**char**。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_ostream](../standard-library/basic-ostream-class.md)，专用于类型的元素**char**具有默认字符特征。

## <a name="wostream"></a>  wostream

创建类型上专用化的 basic_ostream **wchar_t**并`char_traits`专用于**wchar_t**。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_ostream](../standard-library/basic-ostream-class.md)，专用于类型的元素**wchar_t**具有默认字符特征。

## <a name="see-also"></a>请参阅

[\<ostream>](../standard-library/ostream.md)<br/>
