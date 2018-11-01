---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: fcfb020bab2cb85b13caac9cdceee2359a7294d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476561"
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
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|一种类型`basic_filebuf`专用于**char**模板参数。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|一种类型`basic_fstream`专用于**char**模板参数。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|一种类型`basic_ifstream`专用于**char**模板参数。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|一种类型`basic_ofstream`专用于**char**模板参数。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|一种类型`basic_fstream`专用于**wchar_t**模板参数。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|一种类型`basic_ifstream`专用于**wchar_t**模板参数。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|一种类型`basic_ofstream`专用于**wchar_t**模板参数。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|一种类型`basic_filebuf`专用于**wchar_t**模板参数。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|该模板类描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与外部文件中存储的元素序列之间的来回传输进行控制的流缓冲区。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|此模板类描述控制元素的插入和提取的对象和编码的对象使用类的流缓冲区[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**， **Tr**>，类型的元素`Elem`，其字符特征由类`Tr`。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|此模板类描述一个对象，用于控制提取元素和编码的对象类的流缓冲区[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**， **Tr**>，类型的元素`Elem`，其字符特征由类`Tr`。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|此模板类描述类的流缓冲区控制元素插入的对象和编码的对象[basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**， **Tr**>，类型的元素`Elem`，其字符特征由类`Tr`。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
