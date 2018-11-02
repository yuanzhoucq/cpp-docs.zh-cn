---
title: 输入 / 输出流
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: d426baacb52095ab2d933263fdac8e312fc29558
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580197"
---
# <a name="inputoutput-streams"></a>输入/输出流

在头文件 \<istream> 中定义的 `basic_iostream` 是处理输入和输出基于字符 I/O 流的对象的类模板。

存在两个定义 `basic_iostream` 的特定于字符的专用化且可使代码读取更容易的 typedef：`iostream`（请勿与头文件 \<iostream> 混淆）是基于 `basic_iostream<char>` 的 I/O 流；`wiostream` 是基于 `basic_iostream<wchar_t>` 的 I/O 流。

有关详细信息，请参阅 [basic_iostream 类](../standard-library/basic-iostream-class.md)、[iostream](../standard-library/basic-iostream-class.md) 和 [wiostream](../standard-library/basic-iostream-class.md)。

类模板 `basic_fstream` 派生自 `basic_iostream`，用于向/从文件流式处理字符数据。

其他一些 typedef 还可提供 `basic_fstream` 的特定于字符的专用化。 它们是`fstream`，这是基于的文件 I/O 流**char**，和`wfstream`，这是基于的文件 I/O 流**wchar_t**。 有关详细信息，请参阅 [basic_fstream 类](../standard-library/basic-fstream-class.md)、[fstream](../standard-library/basic-fstream-class.md) 和 [wfstream](../standard-library/basic-fstream-class.md)。 使用这些 typedef 要求包含头文件 \<fstream>。

> [!NOTE]
> 使用 `basic_fstream` 对象执行文件 I/O 时，尽管基础缓冲区包含为读取和写入单独指定的位置，但是当前输入和当前输出位置绑定在一起，因此，读取某些数据会移动输出位置。

通常使用类模板 `basic_stringstream` 及其一般专用化 `stringstream` 来处理 I/O 流对象，以插入和提取字符数据。 有关详细信息，请参阅 [basic_stringstream Class](../standard-library/basic-stringstream-class.md)。

## <a name="see-also"></a>请参阅

[stringstream](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream 类](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream>](../standard-library/sstream.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
