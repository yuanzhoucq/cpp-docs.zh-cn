---
title: "Active 技术和 Dll |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44dcc58aed4025af2e3e2177e978633c13f0ef20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="active-technology-and-dlls"></a>Active 技术和 DLL
Active 技术使对象服务器得以在 DLL 内完全实现。 此类型的服务器称为进程内服务器。 MFC 不完全支持进程内服务器的可视化编辑的所有功能主要是因为 Active 技术不提供服务器挂钩到容器的主消息循环的方式。 MFC 需要访问容器应用程序的消息循环，以处理快捷键和空闲处理。  
  
 如果你正在编写自动化服务器并且你的服务器没有用户界面，可以使你的服务器成为进程内服务器并将其完全置于 DLL。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [自动化服务器](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)