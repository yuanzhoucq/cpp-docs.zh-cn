---
title: '&lt;fstream&gt; typedef | Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 49c5af53c6d174e7f87f75ad8970726c526db714
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962970"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedef

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

一种类型`basic_filebuf`专用于**char**模板参数。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_filebuf](../standard-library/basic-filebuf-class.md)，专用于类型的元素**char**具有默认字符特征。

## <a name="fstream"></a>  fstream

一种类型`basic_fstream`专用于**char**模板参数。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_fstream](../standard-library/basic-fstream-class.md)，专用于类型的元素**char**具有默认字符特征。

## <a name="ifstream"></a>  ifstream

定义要用于从文件中按顺序读取单字节字符数据的流。 `ifstream` 是模板类专用化的 typedef`basic_ifstream`有关**char**。

此外，还有`wifstream`，专用化的 typedef`basic_ifstream`读取**wchar_t**倍宽字符。 有关详细信息，请参阅 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_ifstream](../standard-library/basic-ifstream-class.md)，专用于具有默认字符特征的 char 类型的元素。 例如

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

一种类型`basic_ofstream`专用于**char**模板参数。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_ofstream](../standard-library/basic-ofstream-class.md)，专用于类型的元素**char**具有默认字符特征。

## <a name="wfstream"></a>  wfstream

一种类型`basic_fstream`专用于**wchar_t**模板参数。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_fstream](../standard-library/basic-fstream-class.md)，专用于类型的元素**wchar_t**具有默认字符特征。

## <a name="wifstream"></a>  wifstream

一种类型`basic_ifstream`专用于**wchar_t**模板参数。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_ifstream](../standard-library/basic-ifstream-class.md)，专用于类型的元素**wchar_t**具有默认字符特征。

## <a name="wofstream"></a>  wofstream

一种类型`basic_ofstream`专用于**wchar_t**模板参数。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_ofstream](../standard-library/basic-ofstream-class.md)，专用于类型的元素**wchar_t**具有默认字符特征。

## <a name="wfilebuf"></a>  wfilebuf

一种类型`basic_filebuf`专用于**wchar_t**模板参数。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>备注

该类型是模板类的同义词[basic_filebuf](../standard-library/basic-filebuf-class.md)，专用于类型的元素**wchar_t**具有默认字符特征。

## <a name="see-also"></a>请参阅

[\<fstream>](../standard-library/fstream.md)<br/>
