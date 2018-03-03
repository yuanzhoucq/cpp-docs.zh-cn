---
title: "更改图像 （图标的图像编辑器） 上文本的字体 |Microsoft 文档"
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
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07dc7d7fd74ad9d4b0229ffef7cf4e96a4ea44b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>更改图像上文本的字体（图标的图像编辑器）
以下过程演示了如何：  
  
-   将文本添加到 Windows 应用程序中的图标  
  
-   操作文本的字体  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>更改图像上文本的字体  
  
1.  创建 c + + Windows 窗体应用程序。 有关详细信息，请参阅[创建 Windows 应用程序项目](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。 [Windows 窗体应用程序模板](http://msdn.microsoft.com/en-us/1babdebf-ab3f-4a64-a608-98499a5b9cea)将添加一个名为默认情况下的 app.ico 到你的项目文件。  
  
2.  在解决方案资源管理器中，双击文件 app.ico。 [图像编辑器](../windows/image-editor-for-icons.md)将打开。  
  
3.  从**映像**菜单上，选择**工具**，然后选择**文本工具**。 [文本工具对话框](../windows/text-tool-dialog-box-image-editor-for-icons.md)将出现。  
  
4.  在文本工具对话框中，键入`C++`空文本区域中。 此文本将显示在一个可调整大小的框，位于 app.ico、 在图像编辑器中的左上角。  
  
5.  在图像编辑器中，将可调整大小框中拖到 app.ico、 来提高你的文本的可读性的中心。  
  
6.  在文本工具对话框中，单击**字体**按钮。 [文本工具字体对话框](../windows/text-tool-font-dialog-box-image-editor-for-icons.md)将出现。  
  
7.  在文本工具的字体对话框中，选择**Times New Roman**从列表中列出的可用字体**字体**列表框。  
  
8.  选择**加粗**从列表中列出的可用字体样式**字体样式**列表框。  
  
9. 选择**10**从列表中的可用点的大小中列出**大小**列表框。  
  
10. 单击**确定**按钮。 文本工具字体对话框将关闭，并且新的字体设置将应用于你的文本。  
  
11. 单击**关闭**文本工具对话框上的按钮。 环绕文本可调整大小的框将消失从图像编辑器中。  
  
## <a name="see-also"></a>请参阅  
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [工具栏](../windows/toolbar-image-editor-for-icons.md)

