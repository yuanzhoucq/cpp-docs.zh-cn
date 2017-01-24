---
title: "Changing the Font of Text on an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "fonts, changing on an image"
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Font of Text on an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的过程是一个如何执行以下操作的示例：  
  
-   向 Windows 应用程序中的图标添加文本  
  
-   操纵文本的字体  
  
### 更改图像上文本的字体  
  
1.  创建一个 C\+\+ Windows 窗体应用程序。  有关详细信息，请参见[创建 Windows 应用程序项目](http://msdn.microsoft.com/zh-cn/b2f93fed-c635-4705-8d0e-cf079a264efa)。  [Windows 窗体应用程序模板](http://msdn.microsoft.com/zh-cn/1babdebf-ab3f-4a64-a608-98499a5b9cea)默认情况下会在项目中添加一个名为 app.ico 的文件。  
  
2.  在解决方案资源管理器中，双击文件 app.ico。  将打开[图像编辑器](../mfc/image-editor-for-icons.md)。  
  
3.  从**“图像”**菜单中选择**“工具”**，然后选择**“文本工具”**。  将显示[“文本工具”对话框](../mfc/text-tool-dialog-box-image-editor-for-icons.md)。  
  
4.  在“文本工具”对话框的空白文本区中键入 `C++`。  此文本将显示在图像编辑器中 app.ico 左上角的一个可调整大小的框中。  
  
5.  在图像编辑器中，将该可调整大小的框拖动到 app.ico 的中央，以增强文本的可读性。  
  
6.  在“文本工具”对话框中单击**“字体”**按钮。  将显示[“文本工具字体”对话框](../mfc/text-tool-font-dialog-box-image-editor-for-icons.md)。  
  
7.  在“文本工具字体”对话框中，从**“字体”**列表框中列出的可用字体列表中选择**“Times New Roman”**。  
  
8.  从**“字体样式”**列表框中列出的可用字体样式列表中选择**“粗体”**。  
  
9. 从**“大小”**列表框中列出的可用字体磅值列表中选择**“10”**。  
  
10. 单击**“确定”**按钮。  “文本工具字体”对话框将关闭，新的字体设置将应用于文本。  
  
11. 单击“文本工具”对话框上的**“关闭”**按钮。  文本周围的可调整大小的框将从图像编辑器中消失。  
  
## 请参阅  
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Toolbar](../mfc/toolbar-image-editor-for-icons.md)