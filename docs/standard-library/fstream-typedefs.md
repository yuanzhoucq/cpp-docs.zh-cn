---
title: "&lt;fstream&gt; typedef | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 4978b0b9f49fd0b0f4125c3dd2f17d07446bc6ac
ms.lasthandoff: 02/24/2017

---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedef
||||  
|-|-|-|  
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|  
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|  
|[wifstream](#wifstream)|[wofstream](#wofstream)|  
  
##  <a name="filebuf"></a>  filebuf  
 专用于 `char` 模板参数的类型 `basic_filebuf`。  
  
```
typedef basic_filebuf<char, char_traits<char>> filebuf;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 [basic_filebuf](../standard-library/basic-filebuf-class.md) 的同义词，专门用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="fstream"></a>  fstream  
 专用于 `char` 模板参数的类型 `basic_fstream`。  
  
```
typedef basic_fstream<char, char_traits<char>> fstream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_fstream](../standard-library/basic-fstream-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="ifstream"></a>  ifstream  
 定义要用于从文件中按顺序读取单字节字符数据的流。 `ifstream` 是将 `basic_ifstream` 的模板类 `char` 进行专用化的 typedef。  
  
 另外，还有 `wifstream`，一种专用化 `basic_ifstream` 以读取 `wchar_t` 倍宽字符的 typedef。 有关详细信息，请参阅 [wifstream](../standard-library/fstream-typedefs.md#wifstream)。  
  
```
typedef basic_ifstream<char, char_traits<char>> ifstream;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 `basic_ifstream` 的同义词，专门用于具有默认字符特征的 char 类型元素。 例如  
  
 `using namespace std;`  
  
 `ifstream infile("existingtextfile.txt");`  
  
 `if (!infile.bad())`  
  
 `{`  
  
 `// Dump the contents of the file to cout.`  
  
 `cout << infile.rdbuf();`  
  
 `infile.close();`  
  
 `}`  
  
##  <a name="ofstream"></a>  ofstream  
 专用于 `char` 模板参数的类型 `basic_ofstream`。  
  
```
typedef basic_ofstream<char, char_traits<char>> ofstream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_ofstream](../standard-library/basic-ofstream-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="wfstream"></a>  wfstream  
 专用于 `wchar_t` 模板参数的类型 `basic_fstream`。  
  
```
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_fstream](../standard-library/basic-fstream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
##  <a name="wifstream"></a>  wifstream  
 专用于 `wchar_t` 模板参数的类型 `basic_ifstream`。  
  
```
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_ifstream](../standard-library/basic-ifstream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
##  <a name="wofstream"></a>  wofstream  
 专用于 `wchar_t` 模板参数的类型 `basic_ofstream`。  
  
```
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```  
  
### <a name="remarks"></a>备注  
 此类型是模板类 [basic_ofstream](../standard-library/basic-ofstream-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
##  <a name="wfilebuf"></a>  wfilebuf  
 专用于 `wchar_t` 模板参数的类型 `basic_filebuf`。  
  
```
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 [basic_filebuf](../standard-library/basic-filebuf-class.md) 的同义词，专门用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
## <a name="see-also"></a>另请参阅  
 [\<fstream>](../standard-library/fstream.md)




