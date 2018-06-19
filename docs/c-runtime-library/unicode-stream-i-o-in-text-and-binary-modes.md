---
title: 文本和二进制模式下的 Unicode 流 I/O | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b89ff3fc752901e9b3cf30c305110b387dc04562
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409048"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>文本和二进制模式下的 Unicode 流 I/O

当对一个以文本模式（默认方式）打开的文件执行 Unicode 流 I/O 例程（例如 fwprintf、fwscanf、fgetwc、fputwc、fgetws 或 fputws）时，将会发生两种字符转换：

- Unicode 转换为 MBCS 或 MBCS 转换为 Unicode。 当 Unicode 流 I/O 函数在文本模式下运行时，源流或目标流将假定为一系列多字节字符。 因此，Unicode 流输入函数将多字节字符转换为宽字符（就像调用 mbtowc 函数一样）。 出于同一原因，Unicode 流输出函数将宽字符转换为多字节字符（就像调用 wctomb 函数一样）。

- 回车-换行符 (CR-LF) 转换。 此转换发生在 MBCS 到 Unicode 的转换之前（对于 Unicode 流输入函数）和 Unicode 到 MBCS 的转换之后（对于 Unicode 流输出函数）。 在输入过程中，每一个回车-换行符组合将转换为单一的换行符。 在输出过程中，每一个换行符将转换为回车-换行符组合。

但是，当 Unicode 流 I/O 函数以二进制模式运行时，该文件将被假定为 Unicode，并且在输入或输出过程中不会发生 CR-LF 转换或字符转换。 为了对 UNICODE 文本文件正确使用 wcin，请使用 _setmode( _fileno( stdin ), _O_BINARY ); 指令。

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
[输入和输出](../c-runtime-library/input-and-output.md)<br/>
