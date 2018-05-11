---
title: 新建工具栏资源对话框 |Microsoft 文档
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
ms.openlocfilehash: 6662fcfab3c9bb1d805e39147bd2838e6bbce5b2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="new-toolbar-resource-dialog-box"></a>“新建工具栏资源”对话框
新建工具栏资源对话框中，可指定的宽度和高度要添加到工具栏资源的按钮。 默认值为 16 × 15 像素。  
  
 用于创建工具栏位图具有的最大宽度为 2048年。 因此，如果你设置**按钮宽度**为 512，只能有四个按钮。 如果宽度设置为 513 后，你只能有三个按钮。  
  
 **按钮宽度**  
 在此处你可以输入从位图资源转换为工具栏资源的工具栏按钮的宽度。 映像被裁剪为的宽度和高度指定，并且颜色调整以使用标准工具栏的颜色 （16 种颜色）。  
  
 **按钮高度**  
 在此处你可以输入从位图资源转换为工具栏资源的工具栏按钮的高度。 映像被裁剪为的宽度和高度指定，并且颜色调整以使用标准工具栏的颜色 （16 种颜色）。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [工具栏按钮属性](../windows/toolbar-button-properties.md)   
 [将位图转换为工具栏](../windows/converting-bitmaps-to-toolbars.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)

