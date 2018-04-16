---
title: "添加资源对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.insertresource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], adding
- Add Resource dialog box
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aab285109b34b1de2187e02956cfff2e5a0ba724
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="add-resource-dialog-box"></a>“添加资源”对话框
使用此对话框将资源添加到 C++ Windows 桌面应用程序项目。  
  
> [!NOTE]
>  此信息不适用于通用 Windows 平台应用中的资源。 有关的详细信息，请参阅[应用资源和资源管理系统](/windows/uwp/app-resources/)。  
  
 资源类型  
 指定你想要创建的资源类型。  
  
 你可以展开光标和对话框资源目录以显示其他资源。 这些资源位于...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct。 如果添加.rct 文件，你必须将它们放在此目录或你必须指定[包括路径](../windows/how-to-specify-include-directories-for-resources.md)它们。 之后，这些文件中的资源将显示在相应类别下的第二层。 可添加的 .rct 文件数没有预设限制。  
  
 显示在树控件顶层的资源是 Visual Studio 提供的默认资源。  
  
 **新建**  
 创建基于你选择了中的类型的资源**资源类型**框。 资源将在适当的编辑器中打开。 例如，如果创建对话框资源，它会在打开[对话框编辑器](../windows/dialog-editor.md)。  
  
 **Import**  
 打开**导入**对话框中，在其中你可以导航到资源你想要导入到当前项目。 可导入位图、图标、光标、HTML 资源文件、声音 (.WAV) 资源文件或自定义资源文件。  
  
 **自定义**  
 打开[新建自定义资源对话框](../windows/new-custom-resource-dialog-box.md)在其中创建自定义资源。 仅可以在二进制编辑器中编辑自定义资源。  
  
## <a name="requirements"></a>惠?  
 无  
  
## <a name="see-also"></a>请参阅  
 [如何：创建资源](../windows/how-to-create-a-resource.md)