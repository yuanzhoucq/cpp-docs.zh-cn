---
title: 关闭文件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 69a0960c1edabab00cb71702acda526ee9ebd798
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326919"
---
# <a name="closing-files"></a>关闭文件

像往常在 I/O 操作中一样，完成文件后，您必须关闭它。

#### <a name="to-close-a-file"></a>关闭文件

1. 使用**关闭**成员函数。 此函数将关闭文件系统文件并刷新缓冲区（如有必要）。

如果你分配了[CFile](../mfc/reference/cfile-class.md)帧上的对象 (如中所示的示例中所示[打开文件](../mfc/opening-files.md))，此对象将自动关闭，然后销毁时超出范围。 请注意，删除 `CFile` 对象不会删除文件系统中的物理文件。

## <a name="see-also"></a>请参阅

[文件](../mfc/files-in-mfc.md)
