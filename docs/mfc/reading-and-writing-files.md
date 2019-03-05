---
title: 读取和写入文件
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: ab1ddc58ec6cc2b67e5843f46afbead3ead54eba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267664"
---
# <a name="reading-and-writing-files"></a>读取和写入文件

如果已经使用 C 运行时库文件处理函数，MFC 读取和写入操作将看起来很熟悉。 本指南介绍了直接从读取和写入直接向`CFile`对象。 您缓冲的可以也不要使用文件 I/O [CArchive](../mfc/reference/carchive-class.md)类。

#### <a name="to-read-from-and-write-to-the-file"></a>若要从读取和写入文件

1. 使用`Read`和`Write`成员函数来读取和写入数据文件中。

     或

1. `Seek`成员函数也是可用于移动到文件中的特定偏移量。

`Read` 采用缓冲区和要读取的字节数的指针，并返回实际读取的字节数。 如果所需的字节数无法读取，因为文件尾 (EOF) 达到，则返回实际读取的字节数。 如果发生任何读取的错误时，将引发异常。 `Write` 类似于`Read`，而不是返回写入的字节数。 如果出现写入错误，包括不能写入指定的所有字节是引发异常。 如果您具有有效`CFile`对象，可以从其读取或写入到它，如下面的示例中所示：

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
>  您通常应执行中的输入/输出操作数**尝试**/**捕获**异常处理块。 有关详细信息，请参阅[异常处理 (MFC)](../mfc/exception-handling-in-mfc.md)。

## <a name="see-also"></a>请参阅

[文件](../mfc/files-in-mfc.md)
