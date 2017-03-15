---
title: "Opening a Resource for Binary Editing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.binary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary data, editing"
  - "resources [Visual Studio], opening for binary editing"
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Opening a Resource for Binary Editing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 打开 Windows 桌面资源进行二进制编辑  
  
1.  在[资源视图](../windows/resource-view-window.md)中，选择要编辑的特定资源文件。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  右键单击该资源，然后在快捷菜单中单击“打开二进制数据”。  
  
    > [!NOTE]
    >  如果使用[资源视图](../windows/resource-view-window.md)窗口打开 Visual Studio 无法识别其格式的资源（如 RCDATA 或自定义资源），则该资源会自动在二进制编辑器中打开。  
  
### 打开托管资源进行二进制编辑  
  
1.  在解决方案资源管理器中，选择要编辑的特定资源文件。  
  
2.  右键单击该资源，然后从快捷菜单选择“打开方式”。  
  
3.  在“打开方式”对话框中，选择“二进制编辑器”。  
  
    > [!NOTE]
    >  你可以使用[图像编辑器和](../mfc/image-editor-for-icons.md)[二进制编辑器](../mfc/binary-editor.md)处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
    > [!NOTE]
    >  有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 ![二进制编辑器](../Image/vcBinaryEditor2.gif "vcBinaryEditor2")  
二进制编辑器中显示的对话框的二进制数据  
  
 只有特定 ASCII 值才会二进制编辑器中进行表示（0x20 到 0x7E）。 扩展字符在二进制编辑器的 ASCII 值部分（右面板）中显示为句点。 “可打印”字符是 ASCII 值 32 到 126。  
  
> [!NOTE]
>  如果要对已在另一个编辑器窗口中进行编辑的资源使用二进制编辑器，请先关闭其他编辑器窗口。  
  
 **要求**  
  
 无  
  
## 请参阅  
 [Binary Editor](../mfc/binary-editor.md)