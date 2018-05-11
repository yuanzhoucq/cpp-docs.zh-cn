---
title: 打开资源进行二进制编辑 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c09cd825a5974422eaf757419f4ce890f5123100
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="opening-a-resource-for-binary-editing"></a>打开资源进行二进制编辑
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>打开 Windows 桌面资源进行二进制编辑  
  
1.  在 [资源视图](../windows/resource-view-window.md)中，选择要编辑的特定资源文件。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  右键单击该资源，然后在快捷菜单中单击“打开二进制数据”  。  
  
    > [!NOTE]
    >  如果使用 [资源视图](../windows/resource-view-window.md) 窗口打开 Visual Studio 无法识别其格式的资源（如 RCDATA 或自定义资源），则该资源会自动在二进制编辑器中打开。  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>打开托管资源进行二进制编辑  
  
1.  在解决方案资源管理器中，选择要编辑的特定资源文件。  
  
2.  右键单击该资源，然后从快捷菜单选择“打开方式”  。  
  
3.  在“打开方式”  对话框中，选择“二进制编辑器” 。  
  
    > [!NOTE]
    >  你可以使用[图像编辑器](../windows/image-editor-for-icons.md)和[二进制编辑器](binary-editor.md)处理的托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
    > [!NOTE]
    >  有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。   
  
 ![二进制编辑器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
二进制编辑器中显示的对话框的二进制数据  
  
 只有特定 ASCII 值才会二进制编辑器中进行表示（0x20 到 0x7E）。 扩展字符在二进制编辑器的 ASCII 值部分（右面板）中显示为句点。 “可打印”字符是 ASCII 值 32 到 126。  
  
> [!NOTE]
>  如果要对已在另一个编辑器窗口中进行编辑的资源使用二进制编辑器，请先关闭其他编辑器窗口。  
  
 **要求**  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [二进制编辑器](binary-editor.md)

