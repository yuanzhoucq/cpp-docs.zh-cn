---
title: 创建新工具栏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor, creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c805fa46b47db5600dad153ffa51ba4f0b25442b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652290"
---
# <a name="creating-new-toolbars"></a>创建新工具栏
### <a name="to-create-a-new-toolbar"></a>若要创建新工具栏  
  
1.  在中**资源**查看，右键单击.rc 文件，然后选择**添加资源**从快捷菜单。 (如果你的.rc 文件中有一个现有工具栏，只需可以右击**工具栏**文件夹，然后选择**插入工具栏**从快捷菜单。)  
  
     > [!NOTE]
     > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在中**添加资源**对话框中，选择**工具栏**中**资源类型**列表，然后单击**新建**。  
  
     如果一个加号 (**+**) 的旁边将出现**工具栏**资源类型，这意味着工具栏模板都可用。 单击加号以展开模板列表中的，选择一个模板，然后单击**新建**。  
  
     \- 或 -  
  
3.  [将现有的位图转换为工具栏](../windows/converting-bitmaps-to-toolbars.md)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 MFC 或 ATL  
  
## <a name="see-also"></a>请参阅  
 [工具栏编辑器](../windows/toolbar-editor.md)