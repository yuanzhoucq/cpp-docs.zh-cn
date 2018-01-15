---
title: "预定义的符号 Id |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e431ce20361a9a7d3d05676d1b9da01b98c07d5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="predefined-symbol-ids"></a>预定义的符号 ID
开始新项目时，根据项目类型预定义了一些符号 ID 供你使用。 这些符号 ID 支持 MFC 等各种库和项目类型。 它们表示通常包含于任何应用程序或硬件项（如鼠标或打印机）动作中的常见任务。  
  
 处理资源时，这些符号 ID 变得很重要。 它们可用于编辑快捷键表，其中一些已与虚拟键相关联。 此外，还提供给你通过[属性窗口](/visualstudio/ide/reference/properties-window)。 你可以将任何预定义的符号 ID 分配给新资源，也可以向它们分配快捷键，与该符号 ID 关联的功能会自动与该密钥组合关联。  
  
 以下具有预定义符号的库将显示为项目的一部分：  
  
-   [MFC 预定义的符号](../windows/mfc-predefined-symbols.md)  
  
-   [ATL 预定义的符号](../windows/atl-predefined-symbols.md)  
  
-   [Win32 预定义符号](../windows/win32-predefined-symbols.md)  
  
    > [!NOTE]
    >  预定义的符号始终是只读的。  
  

  
## <a name="requirements"></a>惠?  
 Win32、MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [符号：资源标识符](../windows/symbols-resource-identifiers.md)