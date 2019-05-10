---
title: 控制流
ms.date: 11/04/2016
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 85c7e1b22519287fbd03d89487d6639f197a8b63
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743310"
---
# <a name="controlling-streams"></a>控制流

[fopen](../c-runtime-library/reference/fopen-wfopen.md) 返回 `FILE` 类型的对象的地址。 您可以将此地址用作多个库函数的 `stream` 参数以对打开的文件执行各种操作。 对于字节流，会像通过调用 [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md) 读取每个字符一样进行所有输入，并且会像通过调用 [fputc](../c-runtime-library/reference/fputc-fputwc.md) 写入每个字符一样进行所有输出。 对于宽流，会像通过调用 [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md) 读取每个字符一样进行所有输入，并且会像通过调用 [fputwc](../c-runtime-library/reference/fputc-fputwc.md) 写入每个字符一样进行所有输出。

可以通过调用 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 关闭文件，之后，`FILE` 对象的地址将无效。

`FILE` 对象存储流的状态，包括：

- 错误指示器通过遇到读取或写入错误的函数设置非零值。

- 文件尾指示器通过在读取时遇到文件尾的函数设置非零值。

- 如果文件可以支持定位请求，则文件位置指示器将在流中指定要读取或写入的下一个字节。

- [流状态](../c-runtime-library/stream-states.md)指定流是否将接受读取和/或写入，以及流是未绑定的、面向字节的还是面向宽度的。

- 转换状态将记住任何部分汇编的或生成的通用多字节字符的状态，以及文件中字节序列的所有移位状态。

- 文件缓冲区指定数组对象的地址和大小，库函数可使用此对象提高对流进行的读取和写入操作的性能。

不要修改存储在 `FILE` 对象中或与该对象一起使用的指定文件缓冲区中的任何值。 不能复制 `FILE` 对象，也不能将副本的地址用作库函数的 `stream` 参数。

## <a name="see-also"></a>请参阅

[文件和流](../c-runtime-library/files-and-streams.md)
