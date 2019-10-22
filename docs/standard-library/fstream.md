---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688042"
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
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|@No__t_0 专用于**char**模板参数的类型。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|@No__t_0 专用于**char**模板参数的类型。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|@No__t_0 专用于**char**模板参数的类型。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|@No__t_0 专用于**char**模板参数的类型。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|一个类型 `basic_fstream` 专用于**wchar_t**模板参数的类型。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|一个类型 `basic_ifstream` 专用于**wchar_t**模板参数的类型。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|一个类型 `basic_ofstream` 专用于**wchar_t**模板参数的类型。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|一个类型 `basic_filebuf` 专用于**wchar_t**模板参数的类型。|

### <a name="classes"></a>类

|实例|描述|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|类模板描述了一个流缓冲区，该缓冲区控制 `Elem` 类型的元素的传输，其字符特征由类 `Tr`、和从存储在外部文件中的一系列元素确定。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|类模板描述了一个对象，该对象使用类[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**， **Tr**> 的流缓冲区控制元素和编码对象的插入和提取，该对象的元素类型 `Elem`，其字符特征由类 `Tr` 确定。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|类模板描述了一个对象，该对象控制从[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**， **Tr**> 类的流缓冲区提取元素和编码对象，其中的元素类型为 `Elem`，其字符特征为由类 `Tr` 确定。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|类模板描述了一个对象，该对象可控制将元素和编码对象插入到类[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**， **Tr**> 的流缓冲区中，其中包含类型 `Elem` 的元素，其字符特征已确定由类 `Tr`。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
