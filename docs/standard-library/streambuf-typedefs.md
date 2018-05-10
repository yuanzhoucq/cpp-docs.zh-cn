---
title: '&lt;streambuf&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8fb1713dfbc2d9766c488f21d324d801a4886d68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

专用化使用 `char` 作为模板参数的 `basic_streambuf`。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>备注

该类型是模板类 [basic_streambuf`char` 的同义词，专门用于具有默认字符特征的 ](../standard-library/basic-streambuf-class.md) 类型的元素。

## <a name="wstreambuf"></a>  wstreambuf

专用化使用 `wchar_t` 作为模板参数的 `basic_streambuf`。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>备注

该类型是模板类 [basic_streambuf`wchar_t` 的同义词，专门用于具有默认字符特征的 ](../standard-library/basic-streambuf-class.md) 类型的元素。

## <a name="see-also"></a>请参阅

[\<streambuf>](../standard-library/streambuf.md)<br/>
