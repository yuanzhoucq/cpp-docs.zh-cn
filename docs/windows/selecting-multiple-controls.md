---
title: 选择多个控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- controls [C++], removing from groups
ms.assetid: efbdbade-0a3a-4328-b36e-a6376c06e8de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aec9785040f0a30150c8399b5059d6d733ad8be2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383826"
---
# <a name="selecting-multiple-controls"></a>选定多个控件

### <a name="to-select-multiple-controls"></a>若要选择多个控件

1. 在中[工具箱窗口](/visualstudio/ide/reference/toolbox)，选择**指针**工具。

2. 拖动指针以绘制你想要在对话框中选择的控件周围的选择框。

   当释放鼠标按钮时内, 和相交所选内容框中选择所有控件。

   \- 或 -

- 按住**Shift**键，然后单击你想要在所选内容中包含的控件。

   \- 或 -

- 按住**Ctrl**键，然后单击你想要在所选内容中包含的控件。

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>若要从所选控件的组中删除控件或控件添加到所选控件的组

1. 与所选控件的组，按住**Shift**密钥，然后单击你想要添加到现有的选定内容或从其中移除的控件。

   > [!NOTE]
   > 按住**Ctrl**键并单击所选内容内的控件将使该控件中所选内容的主要控件。 有关详细信息，请参阅[指定主导控件](../windows/specifying-the-dominant-control.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[“选择”控件](../windows/selecting-controls.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)