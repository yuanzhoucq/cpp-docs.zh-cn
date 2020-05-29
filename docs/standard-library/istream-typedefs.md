---
title: '&lt;istream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: e9228bddcc3b99503b6b5f0e93b5ed6eeed773d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363084"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[伊流](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a><a name="iostream"></a>iostream

专门在`basic_iostream`**字符**上的类型。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_iostream](../standard-library/basic-iostream-class.md)的同义词，专门用于具有默认字符特征的类型**字符**的元素。

## <a name="istream"></a><a name="istream"></a>伊流

专门在`basic_istream`**字符**上的类型。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_istream](../standard-library/basic-istream-class.md)的同义词，专门用于具有默认字符特征的类型**字符**的元素。

## <a name="wiostream"></a><a name="wiostream"></a>威流

专门在`basic_iostream`**wchar_t**上的类型。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_iostream](../standard-library/basic-iostream-class.md)的同义词，专门用于具有默认字符特征**的类型wchar_t**元素。

## <a name="wistream"></a><a name="wistream"></a>威流

专门在`basic_istream`**wchar_t**上的类型。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_istream](../standard-library/basic-istream-class.md)的同义词，专门用于具有默认字符特征的类型**wchar_t**元素。

## <a name="see-also"></a>另请参阅

[\<istream>](../standard-library/istream.md)
