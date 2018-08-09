---
title: 新建工具栏资源对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33c63357f0816fbf0d89058d4151ea5785f6f35a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015015"
---
# <a name="new-toolbar-resource-dialog-box"></a>“新建工具栏资源”对话框
**新建工具栏资源**对话框允许您指定的宽度和高度为工具栏资源要添加的按钮。 默认值为 16 × 15 像素。  
  
 用于创建工具栏位图有 2048年的最大宽度。 因此，如果您设置**按钮宽度**为 512，只能有四个按钮。 如果将宽度设置为 513，您只能有三个按钮。  
  
### <a name="button-width"></a>按钮宽度  
 提供空间以输入将从位图资源转换为工具栏资源的工具栏按钮的宽度。 图像裁剪为的宽度和高度指定，和颜色调整为使用标准工具栏颜色 （16 种颜色）。  
  
### <a name="button-height"></a>按钮高度  
 提供空间以输入将从位图资源转换为工具栏资源的工具栏按钮的高度。 图像裁剪为的宽度和高度指定，和颜色调整为使用标准工具栏颜色 （16 种颜色）。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [工具栏按钮属性](../windows/toolbar-button-properties.md)   
 [将位图转换为工具栏](../windows/converting-bitmaps-to-toolbars.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)