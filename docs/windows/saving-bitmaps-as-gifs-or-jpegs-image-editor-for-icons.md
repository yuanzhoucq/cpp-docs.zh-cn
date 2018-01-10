---
title: "将位图另存为 Gif 或 Jpeg （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.image.editing
dev_langs: C++
helpviewer_keywords:
- .gif files, saving bitmaps as
- jpg files, saving bitmaps as
- jpeg files, saving bitmaps as
- .jpg files, saving bitmaps as
- Image editor [C++], converting image formats
- gif files, saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files, saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3fe626357283dde8d8f283c6d0aa406ec6c1db0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>将位图另存为 GIF 或 JPEG（图标的图像编辑器）
当你创建位图时，格式为位图 (.bmp) 创建映像。 为 GIF 或 JPEG 或其他图形格式，但是，可以保存图像。  
  
> [!NOTE]
>  此过程不适用于图标和光标。  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>若要创建和保存位图为.gif 或.jpeg  
  
1.  从**文件**菜单上，选择**打开**，然后单击**文件**。  
  
2.  在**新文件对话框**，单击**Visual c + +**文件夹，然后选择**位图文件 (.bmp)**中**模板**框中，单击**打开**。  
  
     在中打开位图**映像**编辑器。  
  
3.  根据需要请对新的位图中进行更改。  
  
4.  与在中仍然打开位图**映像**编辑器中，单击**保存*filename*作为.bmp**上**文件**菜单。  
  
5.  在**文件另存为**对话框框中，键入你想要将文件和表示您要在中的文件格式的扩展名的名称**文件名**框。 例如，myfile.gif。  
  
     **请注意**必须创建或打开你项目外的位图，才能将其保存为另一种文件格式。 如果在创建或打开在你项目中，**另存为**命令都将不可用。 有关详细信息，请参阅[查看资源在资源脚本文件之外的项目 （独立）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
6.  单击“保存” 。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="see-also"></a>请参阅  
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)

