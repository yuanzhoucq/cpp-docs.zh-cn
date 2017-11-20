---
title: "关闭文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3833763394eda3ad64f1c72b80bee4d76785d5a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="closing-files"></a>关闭文件
像往常在 I/O 操作中一样，完成文件后，您必须关闭它。  
  
#### <a name="to-close-a-file"></a>关闭文件  
  
1.  使用**关闭**成员函数。 此函数将关闭文件系统文件并刷新缓冲区（如有必要）。  
  
 如果分配[CFile](../mfc/reference/cfile-class.md)帧上的对象 (如所示的示例所示[打开文件](../mfc/opening-files.md))，此对象将自动关闭，然后在超出范围时销毁。 请注意，删除 `CFile` 对象不会删除文件系统中的物理文件。  
  
## <a name="see-also"></a>另请参阅  
 [文件](../mfc/files-in-mfc.md)

