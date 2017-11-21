---
title: "创建 256 色图标或光标 （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- 256-color palette
- cursors, color
- colors, icons
- colors, cursors
- icons, color
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 12baf092d432aff4ac16d00f1877128eef629e14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-256-color-icon-or-cursor-image-editor-for-icons"></a>创建 256 色图标或光标（图标的图像编辑器）
使用图像编辑器，图标和光标可能会调整了大小大 (64 × 64) 使用 256 色调色板，可供选择。 创建资源之后, 设备图像样式处于选中状态。  
  
### <a name="to-create-a-256-color-icon-or-cursor"></a>若要创建 256 色图标或光标  
  
1.  在[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果你已有现有的图像资源在.rc 文件中，如游标，只需可以右键单击**光标**文件夹，然后选择**插入光标**从快捷菜单。)  
  
     **注意：** 如果你的项目尚未包含 .rc 文件，请参阅 [创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**光标**单击**新建**。  
  
3.  上**映像**菜单上，单击**新建设备图像**。  
  
4.  选择所需的 256 色映像样式。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](https://msdn.microsoft.com/library/f45fce5x.aspx)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](https://msdn.microsoft.com/library/xbx3z216.aspx)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](https://msdn.microsoft.com/library/h6270d0z.aspx)。  
  
 **要求**  
  
 无  
  
## <a name="see-also"></a>另请参阅  
 [使用 256 色调色板](../windows/using-the-256-color-palette-image-editor-for-icons.md)   
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

