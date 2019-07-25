---
title: 输入/输出流
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: 3d5344ede3a62375c4c8102d1fc39445518eb0c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455262"
---
# <a name="inputoutput-streams"></a>输入/输出流

在头文件 \<istream> 中定义的 `basic_iostream` 是处理输入和输出基于字符 I/O 流的对象的类模板。

存在两个定义 `basic_iostream` 的特定于字符的专用化且可使代码读取更容易的 typedef：`iostream`（请勿与头文件 \<iostream> 混淆）是基于 `basic_iostream<char>` 的 I/O 流；`wiostream` 是基于 `basic_iostream<wchar_t>` 的 I/O 流。

有关详细信息，请参阅 [basic_iostream 类](../standard-library/basic-iostream-class.md)、[iostream](../standard-library/basic-iostream-class.md) 和 [wiostream](../standard-library/basic-iostream-class.md)。

类模板 `basic_fstream` 派生自 `basic_iostream`，用于向/从文件流式处理字符数据。

其他一些 typedef 还可提供 `basic_fstream` 的特定于字符的专用化。 它们是一个文件 i/o 流, 它基于**char** `wfstream`和, 后者是一个基于 wchar_t 的文件 i/o 流。  `fstream` 有关详细信息，请参阅 [basic_fstream 类](../standard-library/basic-fstream-class.md)、[fstream](../standard-library/basic-fstream-class.md) 和 [wfstream](../standard-library/basic-fstream-class.md)。 使用这些 typedef 要求包含头文件 \<fstream>。

> [!NOTE]
> 使用 `basic_fstream` 对象执行文件 I/O 时，尽管基础缓冲区包含为读取和写入单独指定的位置，但是当前输入和当前输出位置绑定在一起，因此，读取某些数据会移动输出位置。

通常使用类模板 `basic_stringstream` 及其一般专用化 `stringstream` 来处理 I/O 流对象，以插入和提取字符数据。 有关详细信息，请参阅 [basic_stringstream Class](../standard-library/basic-stringstream-class.md)。

## <a name="see-also"></a>请参阅

[stringstream](../standard-library/basic-stringstream-class.md)\
[basic_stringstream Class](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
