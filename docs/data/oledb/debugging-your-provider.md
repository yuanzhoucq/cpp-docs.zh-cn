---
title: 调试提供程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6258ddd3fd4317c608cb20486c364918fb5c73a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106384"
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