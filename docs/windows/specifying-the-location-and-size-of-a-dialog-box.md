---
title: 指定的位置和一个对话框的大小 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3a3a9a629ec138659a7b0d2aba2460aced31fc74
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648998"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>指定对话框的位置和大小
位置和大小的对话框中，并将位置和大小的控件，以对话框单元为单位测量。 当选择 Visual Studio 状态栏的右下角显示各个控件和对话框中的值。  
  
 有三个属性，您可以在设置[属性窗口](/visualstudio/ide/reference/properties-window)指定对话框将出现在屏幕上。 Center 属性是一个布尔值;如果将值设置为 True，对话框中将始终显示在屏幕的中心。 如果将其设置为 False 时，你可以然后设置 XPos 和 YPos 属性来显式定义在屏幕上将显示此对话框。 位置属性是从定义为 {X = 0，Y = 0} 的查看区域的左上角的偏移量的值。 位置也基于**Absolute Align**属性： 如果为 True，坐标是相对于屏幕的; 如果为 False，坐标是相对于对话框所有者窗口。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)