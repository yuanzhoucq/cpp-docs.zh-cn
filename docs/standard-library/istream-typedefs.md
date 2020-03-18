---
title: '&lt;istream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 9a25e4aa9ee42ea36d1bb8d6b196b36ff5c97758
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425675"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>iostream

在**char**`basic_iostream` 专用化的类型。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_iostream](../standard-library/basic-iostream-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="istream"></a>istream

在**char**`basic_istream` 专用化的类型。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_istream](../standard-library/basic-istream-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="wiostream"></a>wiostream

**Wchar_t**`basic_iostream` 专用化的类型。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_iostream](../standard-library/basic-iostream-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="wistream"></a> wistream

**Wchar_t**`basic_istream` 专用化的类型。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_istream](../standard-library/basic-istream-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="see-also"></a>另请参阅

[\<istream>](../standard-library/istream.md)
