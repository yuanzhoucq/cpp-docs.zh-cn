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
ms.openlocfilehash: f68fd5c48bce214329437cc13fc39da0c3ca7d2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228578"
---
# <a name="reading-and-writing-files"></a>读取和写入文件

如果已使用 C 运行时库文件处理函数，将会熟悉 MFC 读取和写入操作。 本文介绍如何直接从对象读取和向其写入 `CFile` 。 还可以对[CArchive](../mfc/reference/carchive-class.md)类执行缓冲文件 i/o。

#### <a name="to-read-from-and-write-to-the-file"></a>从文件读取和写入文件

1. 使用 `Read` 和 `Write` 成员函数在文件中读取和写入数据。

     -或-

1. `Seek`成员函数还可用于移动到文件中的特定偏移量。

`Read`获取一个指向缓冲区的指针和读取的字节数，并返回所读取的实际字节数。 如果无法读取所需的字节数，因为已达到文件尾（EOF），则返回读取的实际字节数。 如果出现任何读取错误，则会引发异常。 `Write`类似于 `Read` ，但不返回写入的字节数。 如果发生写入错误（包括不写入所有指定的字节），则会引发异常。 如果你有一个有效的 `CFile` 对象，则可以对其进行读取或写入，如以下示例中所示：

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> 通常应在 **`try`** / 异常处理块中执行输入/输出操作 **`catch`** 。 有关详细信息，请参阅[异常处理（MFC）](../mfc/exception-handling-in-mfc.md)。

## <a name="see-also"></a>另请参阅

[文件](../mfc/files-in-mfc.md)
