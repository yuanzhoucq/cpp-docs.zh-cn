---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866207"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

使用**char**作为模板参数的 `basic_streambuf` 的专用化。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_streambuf](../standard-library/basic-streambuf-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="wstreambuf"></a>  wstreambuf

使用**wchar_t**作为模板参数的 `basic_streambuf` 的专用化。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_streambuf](../standard-library/basic-streambuf-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="see-also"></a>另请参阅

[\<streambuf>](../standard-library/streambuf.md)
