---
title: '&lt;sstream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::istringstream
- iosfwd/std::ostringstream
- iosfwd/std::stringbuf
- iosfwd/std::stringstream
- iosfwd/std::wistringstream
- iosfwd/std::wostringstream
- iosfwd/std::wstringbuf
- iosfwd/std::wstringstream
ms.assetid: d102edd2-ecea-4a35-a398-cf96e58dd422
ms.openlocfilehash: c25d3fa66b5105ad2e1ff5a08ebdde90d1d156be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336634"
---
# <a name="ltsstreamgt-typedefs"></a>&lt;sstream&gt; typedef

||||
|-|-|-|
|[伊弦流](#istringstream)|[ostringstream](#ostringstream)|[弦布夫](#stringbuf)|
|[字符串流](#stringstream)|[温斯特林流](#wistringstream)|[沃斯特林流](#wostringstream)|
|[温格布夫](#wstringbuf)|[wstringstream](#wstringstream)|

## <a name="istringstream"></a><a name="istringstream"></a>伊弦流

创建专用于`basic_istringstream`**字符**模板参数的类型。

```cpp
typedef basic_istringstream<char> istringstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_istringstream](../standard-library/basic-istringstream-class.md)的同义词，专用于**字符**类型的元素。

## <a name="ostringstream"></a><a name="ostringstream"></a>奥弦流

创建专用于`basic_ostringstream`**字符**模板参数的类型。

```cpp
typedef basic_ostringstream<char> ostringstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ostringstream](../standard-library/basic-ostringstream-class.md)的同义词，专用于**字符**类型的元素。

## <a name="stringbuf"></a><a name="stringbuf"></a>弦布夫

创建专用于`basic_stringbuf`**字符**模板参数的类型。

```cpp
typedef basic_stringbuf<char> stringbuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_stringbuf](../standard-library/basic-stringbuf-class.md)的同义词，专用于**字符**类型的元素。

## <a name="stringstream"></a><a name="stringstream"></a>字符串流

创建专用于`basic_stringstream`**字符**模板参数的类型。

```cpp
typedef basic_stringstream<char> stringstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_stringstream](../standard-library/basic-stringstream-class.md)的同义词，专用于**字符**类型的元素。

## <a name="wistringstream"></a><a name="wistringstream"></a>温斯特林流

创建专用于`basic_istringstream`**wchar_t**模板参数的类型。

```cpp
typedef basic_istringstream<wchar_t> wistringstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_istringstream](../standard-library/basic-istringstream-class.md)的同义词，专门用于**类型wchar_t**的元素。

## <a name="wostringstream"></a><a name="wostringstream"></a>沃斯特林流

创建专用于`basic_ostringstream`**wchar_t**模板参数的类型。

```cpp
typedef basic_ostringstream<wchar_t> wostringstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ostringstream](../standard-library/basic-ostringstream-class.md)的同义词，专门用于**类型wchar_t**的元素。

## <a name="wstringbuf"></a><a name="wstringbuf"></a>温格布夫

创建专用于`basic_stringbuf`**wchar_t**模板参数的类型。

```cpp
typedef basic_stringbuf<wchar_t> wstringbuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_stringbuf](../standard-library/basic-stringbuf-class.md)的同义词，专门用于**类型wchar_t**的元素。

## <a name="wstringstream"></a><a name="wstringstream"></a>wstringstream

创建专用于`basic_stringstream`**wchar_t**模板参数的类型。

```cpp
typedef basic_stringstream<wchar_t> wstringstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_stringstream](../standard-library/basic-stringstream-class.md)的同义词，专门用于**类型wchar_t**的元素。

## <a name="see-also"></a>另请参阅

[\<溪流>](../standard-library/sstream.md)
