---
title: 拖放框架窗口中的文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa326dba7772ddcdccb304900df4460ce9754665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>拖放框架窗口中的文件
框架窗口管理与文件资源管理器或文件管理器的关系。  
  
 通过重写中添加一些初始化调用`CWinApp`成员函数`InitInstance`中所述， [CWinApp： 应用程序类](../mfc/cwinapp-the-application-class.md)，你可以将你的框架窗口间接打开文件从文件拖放资源管理器或文件管理器，在框架窗口中删除。 请参阅[文件管理器拖放](../mfc/special-cwinapp-services.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)

