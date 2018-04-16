---
title: "对齐参考线上的控件 |Microsoft 文档"
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
- DLUs (dialog units)
- controls [C++], aligning
- Dialog editor, snap to guides
- guides, tick mark interval
- dialog box controls, placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eed9acf533939d305e42478bb87307bc0a055d3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="aligning-controls-on-a-guide"></a>在参考线上对齐控件
当控件移，并参考线对齐控件 （如果不有任何控件的指南以前对齐），参考线对齐控件的尺寸控点。 当移动参考线时，会对齐到它的控件以及移动。 如果移动其中一个指南，对齐到多个指南的控件的大小。  
  
 由对话框单元 (Dlu) 定义确定指南和控件的间距标尺中的刻度线。 DLU 基于对话框字体，通常 8 点 MS Shell Dlg 的大小。 水平 DLU 是由 4 个划分对话框字体的平均宽度。 垂直 DLU 是平均除以八个字体的高度。  
  
### <a name="to-size-a-group-of-controls-with-guides"></a>若要调整的一组控件大小使用指南  
  
1.  与参考线对齐 （或多个控件） 的一侧。  
  
2.  拖动 （或多个控件） 的另一端的指南。  
  
     在必要时使用多个控件，调整大小以与第二个参考线对齐。  
  
3.  移动任一参考线大小 （或多个控件）。  
  
### <a name="to-change-the-intervals-of-the-tick-marks"></a>若要更改的刻度线间隔  
  
1.  从**格式**菜单上，选择**参考线设置**。  
  
2.  在[参考线设置对话框中](../windows/guide-settings-dialog-box.md)中**网格间距**字段中，指定新的宽度和高度 Dlu。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框编辑器状态 （参考线和网格）](../windows/dialog-editor-states-guides-and-grids.md)   
 [对话框中的控件](../windows/controls-in-dialog-boxes.md)

