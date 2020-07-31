---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 3c5dbefba8e2106c6e3e678002bce26fffd26a62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215616"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

`basic_streambuf`使用作为模板参数的的专用化 **`char`** 。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_streambuf](../standard-library/basic-streambuf-class.md)的同义词，专用于 **`char`** 具有默认字符特征的类型的元素。

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf

`basic_streambuf`使用作为模板参数的的专用化 **`wchar_t`** 。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_streambuf](../standard-library/basic-streambuf-class.md)的同义词，专用于 **`wchar_t`** 具有默认字符特征的类型的元素。

## <a name="see-also"></a>另请参阅

[\<streambuf>](../standard-library/streambuf.md)
