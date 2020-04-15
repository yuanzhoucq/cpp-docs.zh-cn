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
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371802"
---
# <a name="reading-and-writing-files"></a>读取和写入文件

如果您已使用 C 运行时库文件处理函数，则 MFC 读取和写入操作将显得熟悉。 本文介绍直接从`CFile`对象读取和写入对象。 您还可以使用[CArchive](../mfc/reference/carchive-class.md)类执行缓冲文件 I/O。

#### <a name="to-read-from-and-write-to-the-file"></a>从中读取和写入文件

1. 使用`Read`和`Write`成员函数读取和写入文件中的数据。

     -或-

1. 成员`Seek`函数还可用于移动到文件中的特定偏移量。

`Read`获取指向缓冲区的指针和要读取的字节数，并返回读取的字节的实际数。 如果由于达到文件结尾 （EOF） 而无法读取所需的字节数，则返回实际读取的字节数。 如果发生任何读取错误，将引发异常。 `Write`与 类似`Read`，但不会返回写入的字节数。 如果发生写入错误（包括未写入指定的所有字节），则引发异常。 如果您有一个有效的`CFile`对象，则可以从对象读取或写入它，如以下示例所示：

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> 通常应在**尝试**/**捕获**异常处理块内执行输入/输出操作。 有关详细信息，请参阅[异常处理 （MFC）。](../mfc/exception-handling-in-mfc.md)

## <a name="see-also"></a>另请参阅

[文件](../mfc/files-in-mfc.md)
