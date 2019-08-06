---
title: '&lt;istream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 864854fa2697a76c2f3476bcb050d5f5d084dc9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458751"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>iostream

在`basic_iostream` **char**上专用化的类型。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_iostream](../standard-library/basic-iostream-class.md)的同义词, 专用于具有默认字符特征的**char**类型的元素。

## <a name="istream"></a>istream

在`basic_istream` **char**上专用化的类型。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_istream](../standard-library/basic-istream-class.md)的同义词, 专用于具有默认字符特征的**char**类型的元素。

## <a name="wiostream"></a>wiostream

在`basic_iostream` **wchar_t**上专用化的类型。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_iostream](../standard-library/basic-iostream-class.md)的同义词, 专用于具有默认字符特征的**wchar_t**类型的元素。

## <a name="wistream"></a> wistream

在`basic_istream` **wchar_t**上专用化的类型。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>备注

该类型是模板类[basic_istream](../standard-library/basic-istream-class.md)的同义词, 专用于具有默认字符特征的**wchar_t**类型的元素。

## <a name="see-also"></a>请参阅

[\<istream>](../standard-library/istream.md)
