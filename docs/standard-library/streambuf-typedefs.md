---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 505739861771a05dd39741f432579a6e9b2d0c26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664056"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

专用化`basic_streambuf`，它使用**char**作为模板参数。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_streambuf](../standard-library/basic-streambuf-class.md)，专用于类型的元素**char**具有默认字符特征。

## <a name="wstreambuf"></a>  wstreambuf

专用化`basic_streambuf`，它使用**wchar_t**作为模板参数。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_streambuf](../standard-library/basic-streambuf-class.md)，专用于类型的元素**wchar_t**具有默认字符特征。

## <a name="see-also"></a>请参阅

[\<streambuf>](../standard-library/streambuf.md)<br/>
