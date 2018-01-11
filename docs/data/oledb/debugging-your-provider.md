---
title: "调试提供程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cfcb90daaf23a5fd8e248d43b920340e38d8057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-your-provider"></a>调试提供程序
有两种方法来调试你的提供商：  
  
-   由于提供程序在进程中创建的你可以创建一些通常使用的 OLE DB 使用者模板和单步执行该提供程序的使用者代码。  
  
-   你可以使用 Visual c + + 附带 ITEST 实用工具。  
  
### <a name="to-use-the-itest-utility"></a>若要使用 ITEST 实用工具  
  
1.  打开提供程序项目。  
  
2.  上**项目**菜单上，单击**设置**。  
  
3.  在**属性页**对话框中，单击**调试**选项卡。  
  
4.  在**调试会话的可执行文件**框中，选择 ITEST 应用程序。  
  
5.  设置断点，并像通常那样调试。  
  
## <a name="see-also"></a>请参阅  
 [使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)