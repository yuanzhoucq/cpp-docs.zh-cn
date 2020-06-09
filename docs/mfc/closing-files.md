---
title: 关闭文件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 51e51c88260a51ec44f11ecb5c2a88e645194f4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617231"
---
# <a name="closing-files"></a>关闭文件

像往常在 I/O 操作中一样，完成文件后，您必须关闭它。

#### <a name="to-close-a-file"></a>关闭文件

1. 使用**Close**成员函数。 此函数将关闭文件系统文件并刷新缓冲区（如有必要）。

如果在帧上分配了[CFile](reference/cfile-class.md)对象（如[打开文件](opening-files.md)中所示的示例中所示），则当对象超出范围时，将自动关闭并销毁该对象。 请注意，删除 `CFile` 对象不会删除文件系统中的物理文件。

## <a name="see-also"></a>另请参阅

[文件](files-in-mfc.md)
