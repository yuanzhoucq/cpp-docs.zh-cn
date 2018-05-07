---
title: 关闭文件 |Microsoft 文档
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
ms.openlocfilehash: 97bd910ae4cb514cda07dd319f37a05a32712909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="closing-files"></a>关闭文件
像往常在 I/O 操作中一样，完成文件后，您必须关闭它。  
  
#### <a name="to-close-a-file"></a>关闭文件  
  
1.  使用**关闭**成员函数。 此函数将关闭文件系统文件并刷新缓冲区（如有必要）。  
  
 如果分配[CFile](../mfc/reference/cfile-class.md)帧上的对象 (如所示的示例所示[打开文件](../mfc/opening-files.md))，此对象将自动关闭，然后在超出范围时销毁。 请注意，删除 `CFile` 对象不会删除文件系统中的物理文件。  
  
## <a name="see-also"></a>请参阅  
 [文件](../mfc/files-in-mfc.md)

