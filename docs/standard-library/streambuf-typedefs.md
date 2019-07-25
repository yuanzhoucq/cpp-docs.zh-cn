---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 178b489d92a4ed7340084490329fdf8fa16c2aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449592"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

使用 char 作为`basic_streambuf`模板参数的的专用化。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_streambuf](../standard-library/basic-streambuf-class.md)的同义词, 专用于具有默认字符特征的**char**类型的元素。

## <a name="wstreambuf"></a>  wstreambuf

使用 wchar_t 作为`basic_streambuf`模板参数的的专用化。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_streambuf](../standard-library/basic-streambuf-class.md)的同义词, 专用于具有默认字符特征的**wchar_t**类型的元素。

## <a name="see-also"></a>请参阅

[\<streambuf>](../standard-library/streambuf.md)
