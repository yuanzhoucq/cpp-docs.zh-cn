---
title: 二进制编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [Visual Studio], editing
- resource editors, Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aa381c42f03bcc77575464af8f8c53ca83e0af81
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650061"
---
# <a name="binary-editor"></a>二进制编辑器
> [!WARNING]
>  **二进制编辑器**在 Express 版本中不可用。  
  
 使用二进制编辑器，可在二进制级别编辑十六进制或 ASCII 格式的所有资源。 还可以使用 [查找命令](/visualstudio/ide/reference/find-command) 来搜索 ASCII 字符串或十六进制字节。 应使用**二进制**编辑器仅当您需要查看或进行次要更改为自定义资源或资源类型不受 Visual Studio 环境。  
  
 若要打开**二进制编辑器**，首先选择**文件** > **新建** > **文件**从主菜单中，选择你想要编辑，然后单击下拉箭头旁的文件**开放**按钮，然后选择**打开** > **二进制编辑器**。  
  
> [!CAUTION]
>  编辑对话框、图像或二进制编辑器中的菜单等资源是很危险的。 不正确的编辑可能会损坏资源，导致其在其本机编辑器中无法读取。  
  
> [!TIP]
>  使用时**二进制**编辑器中的，在许多情况下，你可以右击以显示特定于资源的命令的快捷菜单。 可用命令取决于所指向的光标。 例如，如果单击指向**二进制**时选择了十六进制值编辑器中的，快捷菜单会显示**剪切**，**复制**，和**粘贴**命令。  
  
 与**二进制**编辑器，你可以：  
  
-   [打开资源进行二进制编辑](../windows/opening-a-resource-for-binary-editing.md)  
  
-   [编辑二进制数据](../windows/editing-binary-data.md)  
  
-   [查找二进制数据](../windows/finding-binary-data.md)  
  
-   [创建新的自定义资源或数据资源](../windows/creating-a-new-custom-or-data-resource.md)  
  
## <a name="managed-resources"></a>托管资源  
 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并**二进制**托管项目的编辑器来处理资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [资源编辑器](../windows/resource-editors.md)