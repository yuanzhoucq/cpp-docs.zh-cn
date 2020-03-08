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
ms.openlocfilehash: 3f4104b28f5becfdbf62ede16faa81e855fcac8c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876108"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

`basic_filebuf` 专用于**char**模板参数的类型。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_filebuf](../standard-library/basic-filebuf-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="fstream"></a>  fstream

`basic_fstream` 专用于**char**模板参数的类型。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_fstream](../standard-library/basic-fstream-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="ifstream"></a>  ifstream

定义要用于从文件中按顺序读取单字节字符数据的流。 `ifstream` 是一种为**char**的类模板 `basic_ifstream` 专用化的 typedef。

还有 `wifstream`的 typedef，专用化 `basic_ifstream` 读取**wchar_t**的双字符。 有关详细信息，请参阅 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

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

## <a name="ofstream"></a>  ofstream

`basic_ofstream` 专用于**char**模板参数的类型。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ofstream](../standard-library/basic-ofstream-class.md)的同义词，专用于具有默认字符特征的**char**类型的元素。

## <a name="wfstream"></a>  wfstream

`basic_fstream` 专用于**wchar_t**模板参数的类型。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_fstream](../standard-library/basic-fstream-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="wifstream"></a>  wifstream

`basic_ifstream` 专用于**wchar_t**模板参数的类型。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ifstream](../standard-library/basic-ifstream-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="wofstream"></a>  wofstream

`basic_ofstream` 专用于**wchar_t**模板参数的类型。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>备注

类型是类模板[basic_ofstream](../standard-library/basic-ofstream-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="wfilebuf"></a>  wfilebuf

`basic_filebuf` 专用于**wchar_t**模板参数的类型。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>备注

类型是类模板[basic_filebuf](../standard-library/basic-filebuf-class.md)的同义词，专用于**wchar_t**具有默认字符特征的类型的元素。

## <a name="see-also"></a>另请参阅

[\<fstream>](../standard-library/fstream.md)
