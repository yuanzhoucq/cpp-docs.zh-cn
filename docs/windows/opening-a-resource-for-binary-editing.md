---
title: 打开资源进行二进制编辑 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary
helpviewer_keywords:
- binary data, editing
- resources [C++], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
ms.openlocfilehash: cc66c9d06a8549984e9347af776c56883f8e22f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491177"
---
# <a name="opening-a-resource-for-binary-editing-c"></a>打开资源进行二进制编辑 （c + +）

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>打开 Windows 桌面资源进行二进制编辑

1. 在 [资源视图](../windows/resource-view-window.md)中，选择要编辑的特定资源文件。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 右键单击该资源，然后在快捷菜单中单击“打开二进制数据”  。

   > [!NOTE]
   > 如果您使用[资源视图](../windows/resource-view-window.md)中自动打开窗口，Visual Studio 无法识别 （如 RCDATA 或自定义资源），该资源的格式打开资源**二进制**编辑器。

### <a name="to-open-a-managed-resource-for-binary-editing"></a>打开托管资源进行二进制编辑

1. 在中**解决方案资源管理器**，选择你想要编辑的特定资源文件。

2. 右键单击该资源，然后从快捷菜单选择“打开方式”  。

3. 在“打开方式”  对话框中，选择“二进制编辑器” 。

   > [!NOTE]
   > 可以使用[的图像编辑器](../windows/image-editor-for-icons.md)并[二进制编辑器](binary-editor.md)来处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。

   > [!NOTE]
   > 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

![二进制编辑器](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
二进制编辑器中显示的对话框的二进制数据

只有特定 ASCII 值才会二进制编辑器中进行表示（0x20 到 0x7E）。 扩展字符在二进制编辑器的 ASCII 值部分（右面板）中显示为句点。 “可打印”字符是 ASCII 值 32 到 126。

> [!NOTE]
> 如果你想要使用**二进制**上已在另一个编辑器窗口中，编辑的资源编辑器先关闭其他编辑器窗口。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[二进制编辑器](binary-editor.md)