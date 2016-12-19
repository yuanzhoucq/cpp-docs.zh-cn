---
title: "如何：自定义快速访问工具栏 | Microsoft Docs"
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
helpviewer_keywords: 
  - "快速访问工具栏, 自定义"
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：自定义快速访问工具栏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

快速访问工具栏 \(QAT\) 是包含一组命令的自定义工具栏，显示在应用程序按钮旁边或者在分类标签下。  下图显示了一个典型的快速访问工具栏。  
  
 ![MFC 功能区快速访问工具栏](../mfc/media/quick_access_toolbar.png "Quick\_Access\_Toolbar")  
  
 若要自定义快速访问工具栏，请**属性** 窗口中打开它，修改其命令，然后预览功能区控件。  
  
### 在属性窗口中打开快速访问工具栏  
  
1.  在 Visual Studio 中，在 **视图** 菜单上，单击 **资源视图**。  
  
2.  在 **资源视图**中，在设计界面双击功能区资源查看它。  
  
3.  在设计图面上，右击快速访问工具栏菜单然后单击 **属性**。  
  
## 快速访问工具栏属性  
 下表定义快速访问工具栏的属性。  
  
|Property|定义|  
|--------------|--------|  
|QAT位置|当应用程序启动时指定快速访问工具栏的位置。  位置可以是 **上方** 或 **靠下** 功能区控件。|  
|QAT 项|指定快速访问工具栏是可用的命令。|  
  
#### 添加或移除在快速访问工具栏中上的命令  
  
1.  在**“属性”**窗口中，单击**QAT Items**，然后单击省略号按钮**“...”**。  
  
2.  在 **QAT 项编辑器** 对话框中，使用 **添加** 和 **移除** 命令按钮修改在快速访问工具栏上的命令列表。  
  
3.  如果希望命令显示在快速访问工具栏和快速访问工具栏菜单中，请选择命令旁边选择框。  如果您想让命令只出现在菜单中，请清除框。  
  
## 预览功能区  
 快速访问工具栏命令没有出现在设计图面上。  若要查看这些属性，您必须预览功能区或运行应用程序。  
  
#### 预览功能区控件  
  
-   在**“功能区编辑器工具栏”**上，单击**“测试功能区”**。  
  
## 请参阅  
 [功能区设计器 \(MFC\)](../mfc/ribbon-designer-mfc.md)