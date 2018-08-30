---
title: 更改图像 （图标的图像编辑器） 上文本的字体 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7a8f06ae0021a95e9b4ae40506cfc91d6a8ae99b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200809"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>更改图像上文本的字体（图标的图像编辑器）

下面的过程是如何的示例：

- 将文本添加到 Windows 应用程序中的图标

- 处理文本的字体

### <a name="to-change-the-font-of-text-on-an-image"></a>若要更改图像上文本的字体

1. 创建 c + + Windows 窗体应用程序。 有关详细信息，请参阅[创建一个 Windows 应用程序项目](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5\(v=vs.100\))。 [Windows 窗体应用程序模板](https://msdn.microsoft.com/1babdebf-ab3f-4a64-a608-98499a5b9cea)将添加一个名为文件`app.ico`到你的项目默认情况下。

2. 在中**解决方案资源管理器**，双击文件 app.ico。 [的图像编辑器](../windows/image-editor-for-icons.md)将打开。

3. 从**图像**菜单中，选择**工具**，然后选择**文本工具**。 [文本工具对话框](../windows/text-tool-dialog-box-image-editor-for-icons.md)将出现。

4. 在中**文本工具**对话框中，键入`C++`空文本区域中。 此文本将显示在一个可调整大小的框，位于左上角`app.ico`，请在**的图像编辑器**。

5. 在中**的图像编辑器**，将可调整大小框中拖到 app.ico，以提高文本可读性的中心。

6. 在中**文本工具**对话框中，单击**字体**按钮。 [文本工具字体对话框](../windows/text-tool-font-dialog-box-image-editor-for-icons.md)将出现。

7. 在中**文本工具字体**对话框中，选择**Times New Roman**从列表中列出的可用字体**字体**列表框。

8. 选择**加粗**从列表中列出的可用字体样式**字体样式**列表框。

9. 选择**10**从列表中的可用点中列出的大小**大小**列表框。

10. 单击**确定**按钮。 **文本工具字体**对话框将关闭，并且新的字体设置将应用于您的文本。

11. 单击**关闭**按钮**文本工具**对话框。 在文本周围的调整大小框将不会出现**的图像编辑器**。

## <a name="see-also"></a>请参阅

[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[工具栏](../windows/toolbar-image-editor-for-icons.md)