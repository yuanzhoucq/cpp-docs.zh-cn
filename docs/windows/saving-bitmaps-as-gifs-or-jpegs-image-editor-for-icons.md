---
title: 将位图另存为 Gif 或 Jpeg （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: debb2b1e8435cc53ec82ab1f957710850d7b5de3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010686"
---
# <a name="saving-bitmaps-as-gifs-or-jpegs-image-editor-for-icons"></a>将位图另存为 GIF 或 JPEG（图标的图像编辑器）
在创建位图时，位图格式 (.bmp) 中创建映像。 但是，，您可以图像保存为 GIF 或 JPEG 或其他图形格式。  
  
> [!NOTE]
>  此过程不适用于图标和光标。  
  
### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>若要创建并将位图另存为.gif 或.jpeg  
  
1.  从**文件**菜单中，选择**打开**，然后单击**文件**。  
  
2.  在中**新文件对话框**，单击**Visual c + +** 文件夹，然后选择**位图文件 (.bmp)** 中**模板**框，然后单击**打开**。  
  
     在中打开位图**图像**编辑器。  
  
3.  根据需要对新的位图进行更改。  
  
4.  与仍在中打开位图**图像**编辑器中，单击**保存*filename*为.bmp**上**文件**菜单。  
  
5.  在**将文件另存为**对话框框中，键入你想要提供的文件和表示中所需的文件格式的扩展插件的名称**文件名**框。 例如， *myfile.gif*。  
  
     > [!NOTE]
     > 必须创建或打开在项目之外的位图，才能将其保存为另一种文件格式。 如果在创建或打开您的项目内**另存为**命令将不可用。 有关详细信息，请参阅[查看资源在资源脚本文件之外的项目 （独立版）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
6.  单击“保存” 。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="see-also"></a>请参阅  
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)