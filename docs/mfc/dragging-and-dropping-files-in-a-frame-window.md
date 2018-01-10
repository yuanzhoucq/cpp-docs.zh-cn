---
title: "拖放框架窗口中的文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 938640ed85e51d2b94b292bfe78a8d912b095188
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>拖放框架窗口中的文件
框架窗口管理与文件资源管理器或文件管理器的关系。  
  
 通过重写中添加一些初始化调用`CWinApp`成员函数`InitInstance`中所述， [CWinApp： 应用程序类](../mfc/cwinapp-the-application-class.md)，你可以将你的框架窗口间接打开文件从文件拖放资源管理器或文件管理器，在框架窗口中删除。 请参阅[文件管理器拖放](../mfc/special-cwinapp-services.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)

