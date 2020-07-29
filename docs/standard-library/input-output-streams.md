---
title: 输入/输出流
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 54b53f96d487e466106fe92a01affa7bd3e55c16
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228253"
---
# <a name="inputoutput-streams"></a>输入/输出流

`basic_iostream`在标头文件中定义的 \<istream> 是用于处理输入和输出基于字符的 i/o 流的对象的类模板。

有两个 typedef 可用于定义的特定于字符的专用化 `basic_iostream` ，并有助于使代码更易于阅读： `iostream` （不与标头文件混淆 \<iostream> ）是基于的 i/o 流 `basic_iostream<char>` ; 是基于的 i/o `wiostream` 流 `basic_iostream<wchar_t>` 。

有关详细信息，请参阅 [basic_iostream 类](../standard-library/basic-iostream-class.md)、[iostream](../standard-library/basic-iostream-class.md) 和 [wiostream](../standard-library/basic-iostream-class.md)。

类模板 `basic_fstream` 派生自 `basic_iostream`，用于向/从文件流式处理字符数据。

其他一些 typedef 还可提供 `basic_fstream` 的特定于字符的专用化。 它们是 `fstream` 基于的文件 i/o 流 **`char`** ，并且是 `wfstream` 基于的文件 i/o 流，后者是基于的文件 i/o 流 **`wchar_t`** 。 有关详细信息，请参阅 [basic_fstream 类](../standard-library/basic-fstream-class.md)、[fstream](../standard-library/basic-fstream-class.md) 和 [wfstream](../standard-library/basic-fstream-class.md)。 使用这些 typedef 需要包含标头文件 \<fstream> 。

> [!NOTE]
> 使用 `basic_fstream` 对象执行文件 I/O 时，尽管基础缓冲区包含为读取和写入单独指定的位置，但是当前输入和当前输出位置绑定在一起，因此，读取某些数据会移动输出位置。

通常使用类模板 `basic_stringstream` 及其一般专用化 `stringstream` 来处理 I/O 流对象，以插入和提取字符数据。 有关详细信息，请参阅 [basic_stringstream Class](../standard-library/basic-stringstream-class.md)。

## <a name="see-also"></a>另请参阅

[stringstream](../standard-library/basic-stringstream-class.md)\
[basic_stringstream 类](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[C + + 标准库](../standard-library/cpp-standard-library-reference.md)
