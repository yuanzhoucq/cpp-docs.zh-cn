---
title: 调试提供程序 |Microsoft Docs
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
ms.openlocfilehash: 5552b9c3d3d697b322b8c1d71eaf0e71630fac38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040173"
---
# <a name="debugging-your-provider"></a>调试提供程序

有两种方法来调试您的提供程序：  
  
- 由于提供程序在进程中创建的可以创建一些通常情况下使用 OLE DB 使用者模板和单步执行该提供程序的使用者代码。  
  
- 可以使用 Visual c + + 附带 ITEST 实用工具。  
  
### <a name="to-use-the-itest-utility"></a>若要使用 ITEST 实用程序  
  
1. 打开提供程序项目。  
  
1. 上**项目**菜单上，单击**设置**。  
  
1. 在中**属性页**对话框中，单击**调试**选项卡。  
  
1. 在中**调试会话的可执行文件**框中，选择 ITEST 应用程序。  
  
1. 设置断点，并像通常那样调试。  
  
## <a name="see-also"></a>请参阅  

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)