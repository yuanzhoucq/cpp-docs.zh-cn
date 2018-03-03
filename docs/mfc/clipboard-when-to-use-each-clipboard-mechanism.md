---
title: "剪贴板： 何时使用每一剪贴板机制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard, guidelines
- Clipboard [MFC], mechanisms
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
- Clipboard [MFC], formats
ms.assetid: fd071996-ef8c-488b-81bd-89057095a201
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e690f3467edd99584137642db8d9c24964ffeb06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-when-to-use-each-clipboard-mechanism"></a>剪贴板：何时使用每一剪贴板机制
请遵循在剪贴板中使用这些准则：  
  
-   使用 OLE 剪贴板机制现在将来启用新功能。 尽管标准剪贴板 API 将保持不变，OLE 机制是未来的数据传输。  
  
-   如果你正在编写 OLE 应用程序或您希望 OLE 功能的任何内容，如拖放，请使用 OLE 剪贴板机制。  
  
-   如果你要提供 OLE 格式，请使用 OLE 剪贴板机制。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么  
  
-   [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [使用 Windows 剪贴板机制](../mfc/clipboard-using-the-windows-clipboard.md)  
  
## <a name="see-also"></a>请参阅  
 [剪贴板](../mfc/clipboard.md)

