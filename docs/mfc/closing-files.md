---
title: 关闭文件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c392ef728e1d796a02cfa32edc2c3e8c74d083b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426232"
---
# <a name="closing-files"></a>关闭文件

像往常在 I/O 操作中一样，完成文件后，您必须关闭它。

#### <a name="to-close-a-file"></a>关闭文件

1. 使用**关闭**成员函数。 此函数将关闭文件系统文件并刷新缓冲区（如有必要）。

如果你分配了[CFile](../mfc/reference/cfile-class.md)帧上的对象 (如中所示的示例中所示[打开文件](../mfc/opening-files.md))，此对象将自动关闭，然后销毁时超出范围。 请注意，删除 `CFile` 对象不会删除文件系统中的物理文件。

## <a name="see-also"></a>请参阅

[文件](../mfc/files-in-mfc.md)

