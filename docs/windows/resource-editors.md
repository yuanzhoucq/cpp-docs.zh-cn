---
title: 资源编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
dev_langs:
- C++
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d1a59befd405e1412c2815694c40c8d24a99cec
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016991"
---
# <a name="resource-editors"></a>资源编辑器
一个**资源**编辑器是用于创建或修改 Visual Studio 项目中包含的资源的专用的环境。 Visual Studio 资源编辑器共享技术和接口，以帮助你快速、轻松地创建和修改应用程序资源。 通过资源编辑器，你可以 [在适当的编辑器中查看和编辑资源](../windows/viewing-and-editing-resources-in-a-resource-editor.md) 并 [预览资源](../windows/previewing-resources.md)。  
  
 创建或打开某个资源时，将自动打开相应的编辑器。  
  
 **注意** 由于托管的项目不使用资源脚本文件，因此你必须从“解决方案资源管理器” 打开资源。 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
|使用...|编辑...|  
|----------------|----------------|  
|[快捷键编辑器](../windows/accelerator-editor.md)|Visual C++ 项目中的快捷键对应表。|  
|[二进制编辑器](binary-editor.md)|二进制数据信息和 Visual C++、Visual Basic 或 Visual C# 项目中的自定义资源。|  
|[对话框编辑器](../windows/dialog-editor.md)|Visual C++ 项目中的对话框。|  
|[图像编辑器](../windows/image-editor-for-icons.md)|Visual C++、Visual Basic 或 Visual C# 项目中的位图、图标、光标以及其他图像文件。|  
|[菜单编辑器](../windows/menu-editor.md)|Visual C++ 项目中的菜单资源。|  
|[Ribbon 编辑器](../mfc/ribbon-designer-mfc.md)|MFC 项目中的功能区资源。|  
|[字符串编辑器](../windows/string-editor.md)|Visual C++ 项目中的字符串表。|  
|[工具栏编辑器](../windows/toolbar-editor.md)|Visual C++ 项目中的工具栏资源。 工具栏编辑器是图像编辑器的一部分。|  
|[版本信息编辑器](../windows/version-information-editor.md)|Visual C++ 项目中的版本信息。|  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [使用资源文件](../windows/working-with-resource-files.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [符号： 资源标识符](../windows/symbols-resource-identifiers.md)   
 [菜单和其他资源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)