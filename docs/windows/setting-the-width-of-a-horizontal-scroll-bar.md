---
title: "设置水平滚动条的宽度 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls, scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars, displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars, width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7aeabed9eaa164a0c19fd6b425f36e68059a548d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>设置水平滚动条的宽度
在水平滚动条在列表框中添加到对话框中使用 MFC 类时，滚动条将不会自动出现在你的应用程序。  
  
### <a name="to-make-the-scroll-bar-appear"></a>若要使滚动条出现  
  
1.  通过调用设置提供给最大元素的最大宽度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)在代码中。  
  
     如果不设置此值后，滚动条将不会出现，甚至时列表框中的项宽于框。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 MFC  
  
## <a name="see-also"></a>请参阅  
 [在对话框中的控件](../windows/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)

