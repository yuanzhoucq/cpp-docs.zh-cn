---
title: "Binary Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.binary.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "editors, Binary"
  - "resources [Visual Studio], editing"
  - "resource editors, Binary editor"
  - "Binary editor"
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Binary Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!WARNING]
>  二进制编辑器在 Express 版本中不可用。  
  
 使用二进制编辑器，可在二进制级别编辑十六进制或 ASCII 格式的所有资源。 还可以使用 [查找命令](../Topic/Find%20Command.md)来搜索 ASCII 字符串或十六进制字节。 只有需要查看 Visual Studio 环境不支持的自定义资源或资源类型或进行细微更改时，才应使用二进制编辑器。  
  
 若要打开二进制编辑器，请先从主菜单中选择**“文件 &#124; 新建 &#124; 文件”**，选择要编辑的文件，然后单击**“打开”**按钮旁边的下拉箭头，并选择**“打开方式 &#124; 二进制编辑器”**。  
  
> [!CAUTION]
>  编辑对话框、图像或二进制编辑器中的菜单等资源是很危险的。 不正确的编辑可能会损坏资源，导致其在其本机编辑器中无法读取。  
  
> [!TIP]
>  使用二进制编辑器时，在许多情况下可以单击鼠标右键以显示资源命令的快捷菜单。 可用命令取决于所指向的光标。 例如，如果在指向二进制编辑器时选择了十六进制值，此时单击鼠标则快捷菜单会显示**剪切**、**复制**和**粘贴**命令。  
  
 使用二进制编辑器，可以执行下列操作：  
  
-   [打开资源进行二进制编辑](../mfc/opening-a-resource-for-binary-editing.md)  
  
-   [编辑二进制数据](../mfc/editing-binary-data.md)  
  
-   [查找二进制数据](../mfc/finding-binary-data.md)  
  
-   [创建新的自定义资源或数据资源](../mfc/creating-a-new-custom-or-data-resource.md)  
  
## 托管资源  
 可以使用[图像编辑器](../mfc/image-editor-for-icons.md)和二进制编辑器处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 无  
  
## 请参阅  
 [Resource Editors](../mfc/resource-editors.md)