---
title: 关闭文件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 04e5084615b1f1cf85d9f41e2c4dcc84910b9d05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636252"
---
# <a name="closing-files"></a>关闭文件

像往常在 I/O 操作中一样，完成文件后，您必须关闭它。

#### <a name="to-close-a-file"></a>关闭文件

1. 使用**关闭**成员函数。 此函数将关闭文件系统文件并刷新缓冲区（如有必要）。

如果你分配了[CFile](../mfc/reference/cfile-class.md)帧上的对象 (如中所示的示例中所示[打开文件](../mfc/opening-files.md))，此对象将自动关闭，然后销毁时超出范围。 请注意，删除 `CFile` 对象不会删除文件系统中的物理文件。

## <a name="see-also"></a>请参阅

[文件](../mfc/files-in-mfc.md)

