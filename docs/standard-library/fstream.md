---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: ba6a4152b8d37f5b0186f9d05c6ba850e8c2e54c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454022"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

定义若干类，这些类支持在存储于外部文件中的序列上的 iostreams 操作。

## <a name="syntax"></a>语法

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|专用于`basic_filebuf` **char**模板参数的类型。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|专用于`basic_fstream` **char**模板参数的类型。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|专用于`basic_ifstream` **char**模板参数的类型。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|专用于`basic_ofstream` **char**模板参数的类型。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|一个专用`basic_fstream`于**wchar_t**模板参数的类型。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|一个专用`basic_ifstream`于**wchar_t**模板参数的类型。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|一个专用`basic_ofstream`于**wchar_t**模板参数的类型。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|一个专用`basic_filebuf`于**wchar_t**模板参数的类型。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|该模板类描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与外部文件中存储的元素序列之间的来回传输进行控制的流缓冲区。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|此模板类描述一个对象, 该对象使用[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 类的流缓冲区控制元素和编码对象的插入和提取, 并使用类型`Elem`的元素进行字符特征由类`Tr`确定。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|此模板类描述一个对象, 该对象控制从[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 类的流缓冲区中提取元素和编码对象, 其中包含类型`Elem`的元素, 其字符特征由类`Tr`确定。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|此模板类描述一个对象, 该对象控制将元素和编码对象插入到类[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**> 的流缓冲区中, 其中包含`Elem`类型的元素, 其字符特征由类`Tr`确定。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
