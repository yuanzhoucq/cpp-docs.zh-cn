---
title: '&lt;fstream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: a0f62f951fb6de4b32a27511ae38e1346cbc22e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215746"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>filebuf

`basic_filebuf`专用于 **`char`** 模板参数的类型。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_filebuf](../standard-library/basic-filebuf-class.md)的同义词，专用于 **`char`** 具有默认字符特征的类型的元素。

## <a name="fstream"></a><a name="fstream"></a>m

`basic_fstream`专用于 **`char`** 模板参数的类型。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_fstream](../standard-library/basic-fstream-class.md)的同义词，专用于 **`char`** 具有默认字符特征的类型的元素。

## <a name="ifstream"></a><a name="ifstream"></a>ifstream

定义要用于从文件中按顺序读取单字节字符数据的流。 `ifstream`是专用化的类模板的 typedef `basic_ifstream` **`char`** 。

此外，还 `wifstream` 提供了一种专用化 `basic_ifstream` 以读取 **`wchar_t`** 双倍宽字符的 typedef。 有关详细信息，请参阅 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ifstream](../standard-library/basic-ifstream-class.md)的同义词，专用于具有默认字符特征的 char 类型的元素。 例如

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>ofstream

`basic_ofstream`专用于 **`char`** 模板参数的类型。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ofstream](../standard-library/basic-ofstream-class.md)的同义词，专用于 **`char`** 具有默认字符特征的类型的元素。

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

`basic_fstream`专用于 **`wchar_t`** 模板参数的类型。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_fstream](../standard-library/basic-fstream-class.md)的同义词，专用于 **`wchar_t`** 具有默认字符特征的类型的元素。

## <a name="wifstream"></a><a name="wifstream"></a>wifstream

`basic_ifstream`专用于 **`wchar_t`** 模板参数的类型。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ifstream](../standard-library/basic-ifstream-class.md)的同义词，专用于 **`wchar_t`** 具有默认字符特征的类型的元素。

## <a name="wofstream"></a><a name="wofstream"></a>wofstream

`basic_ofstream`专用于 **`wchar_t`** 模板参数的类型。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ofstream](../standard-library/basic-ofstream-class.md)的同义词，专用于 **`wchar_t`** 具有默认字符特征的类型的元素。

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf

`basic_filebuf`专用于 **`wchar_t`** 模板参数的类型。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_filebuf](../standard-library/basic-filebuf-class.md)的同义词，专用于 **`wchar_t`** 具有默认字符特征的类型的元素。

## <a name="see-also"></a>另请参阅

[\<fstream>](../standard-library/fstream.md)
