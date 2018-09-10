---
title: 创建一个新对话框 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 285444b5f9bfa29ab00fc6a2ca1b644208bc95a8
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315790"
---
# <a name="creating-a-new-dialog-box-c"></a>创建一个新对话框 （c + +）

### <a name="to-create-a-new-dialog-box"></a>若要创建新的对话框

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**添加资源**从快捷菜单。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在中**添加资源**对话框中，选择**对话框**中**资源类型**列表，然后单击**新建**。

   如果一个加号 (**+**) 的旁边将出现**对话框**资源类型，这意味着对话框模板都可用。 单击加号以展开模板列表中的，选择一个模板，然后单击**新建**。

   在中打开新建对话框**对话框**编辑器。

   此外可以[在对话框编辑器中的现有对话框打开进行编辑](../windows/viewing-and-editing-resources-in-a-resource-editor.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[如何：创建资源](../windows/how-to-create-a-resource.md)  
[资源文件](../windows/resource-files-visual-studio.md)  
[对话框编辑器](../windows/dialog-editor.md)