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
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317193"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[威夫流](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>文件

专门用于`basic_filebuf`**字符**模板参数的类型。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_filebuf](../standard-library/basic-filebuf-class.md)的同义词，专门用于具有默认字符特征的类型**字符**的元素。

## <a name="fstream"></a><a name="fstream"></a>fstream

专门用于`basic_fstream`**字符**模板参数的类型。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_fstream](../standard-library/basic-fstream-class.md)的同义词，专门用于具有默认字符特征的类型**字符**的元素。

## <a name="ifstream"></a><a name="ifstream"></a>如果流

定义要用于从文件中按顺序读取单字节字符数据的流。 `ifstream`是专门用于`basic_ifstream`**字符**的类模板的类型def。

还有`wifstream`，一个专门`basic_ifstream`读取**wchar_t**双宽字符的类型。 有关详细信息，请参阅 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ifstream](../standard-library/basic-ifstream-class.md)的同义词，专门用于具有默认字符特征的类型字符的元素。 例如

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>流

专门用于`basic_ofstream`**字符**模板参数的类型。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ofstream](../standard-library/basic-ofstream-class.md)的同义词，专门用于具有默认字符特征的类型**字符**的元素。

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

专门用于`basic_fstream`**wchar_t**模板参数的类型。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_fstream](../standard-library/basic-fstream-class.md)的同义词，专门用于具有默认字符特征的类型**wchar_t**元素。

## <a name="wifstream"></a><a name="wifstream"></a>威夫流

专门用于`basic_ifstream`**wchar_t**模板参数的类型。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ifstream](../standard-library/basic-ifstream-class.md)的同义词，专门用于具有默认字符特征**的类型wchar_t**元素。

## <a name="wofstream"></a><a name="wofstream"></a>沃夫流

专门用于`basic_ofstream`**wchar_t**模板参数的类型。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_ofstream](../standard-library/basic-ofstream-class.md)的同义词，专门用于具有默认字符特征**的类型wchar_t**元素。

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf

专门用于`basic_filebuf`**wchar_t**模板参数的类型。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>备注

该类型是类模板[basic_filebuf](../standard-library/basic-filebuf-class.md)的同义词，专门用于具有默认字符特征**的类型wchar_t**元素。

## <a name="see-also"></a>另请参阅

[\<>](../standard-library/fstream.md)
