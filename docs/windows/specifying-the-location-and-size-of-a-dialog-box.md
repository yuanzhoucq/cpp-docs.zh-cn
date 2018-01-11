---
title: "指定的位置和大小的对话框中 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03c4c6d6afb13a0e4ed8801838356ff0d1e851f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>指定对话框的位置和大小
位置和大小的对话框中，以及位置和中，控件的大小以对话框单位进行衡量。 当选择 Visual Studio 状态栏的右下方显示单独的控件和对话框中的值。  
  
 有三个您可以在设置的属性[属性窗口](/visualstudio/ide/reference/properties-window)指定对话框中将出现在屏幕上。 Center 属性是布尔型;如果将值设置为 True 时，对话框中将始终显示在屏幕的中心。 如果将其设置为 False 时，你可以然后设置 XPos 和 YPos 属性，以显式定义对话框中将显示在屏幕上的位置。 位置属性是从查看区域中，吞吐量被定义为 {X = 0，Y = 0} 左上角的偏移量的值。 位置还基于**Absolute Align**属性： 如果为 True，坐标相对于屏幕; 如果为 False，坐标相对于对话框所有者窗口。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)

