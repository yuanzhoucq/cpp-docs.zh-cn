---
title: 更改控件的 tab 键顺序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 822e0c5ac0232ac30e4db63b3605fda0126959de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434591"
---
# <a name="changing-the-tab-order-of-controls"></a>更改控件的 Tab 键顺序

Tab 键顺序为依据的顺序**选项卡**键将输入的焦点从一个控件移到下一个对话框中。 通常从左到右、 从上到下一个对话框中，将继续 tab 键顺序。 每个控件都**Tabstop**属性，用于确定控件是否接收输入的焦点。

### <a name="to-set-input-focus-for-a-control"></a>若要设置输入的焦点的控件

1. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，选择**True**或**False**中**Tabstop**属性。

即便是那些不具有**Tabstop**属性设置为**True**需要是 tab 键顺序的一部分。 这可以是重要的是，例如，当您[定义的访问键 （助记键）](../windows/defining-mnemonics-access-keys.md)没有标题的控件。 包含相关控件的访问键的静态文本注释后面必须紧跟相关的控件的 tab 键顺序。

> [!NOTE]
> 如果对话框包含重叠的控件，则更改 tab 键顺序可能会更改控件的显示的方式。 基于任何重叠的控件的 tab 键顺序将它们之前始终显示控件的更高版本中的 tab 键顺序。

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>若要在对话框中查看当前的所有控件的 tab 键顺序

1. 上**格式**菜单上，单击**tab 键顺序**。

\- 或 -

- 按**Ctrl**+**D**。

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>若要更改的对话框中的所有控件的 tab 键顺序

1. 上**格式**菜单上，单击**tab 键顺序**。

   每个控件的左上角的数字的当前选项卡顺序显示其位置。

2. 通过单击所需的顺序在每个控件设置 tab 键顺序**选项卡**键遵循。

3. 按**Enter**退出**tab 键顺序**模式。

   > [!TIP]
   > 一旦您进入**tab 键顺序**模式下，可以按**Esc**或**Enter**可禁止更改 tab 键顺序。

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>若要更改两个或多个控件的 tab 键顺序

1. 从**格式**菜单中，选择**tab 键顺序**。

2. 指定将开始按顺序更改的位置。 若要执行此操作，按下**Ctrl**密钥，然后单击的要更改其顺序开始之前的控件。

   例如，如果你想要更改控件的顺序`7`通过`9`，按住**Ctrl**，然后选择的控件`6`第一个。

   > [!NOTE]
   > 若要将特定控件设置为数字`1`（首先在 tab 键顺序），双击该控件。

3. 发行**Ctrl**键，然后单击所需的顺序中的控件**选项卡**键遵循从该点。

4. 按**Enter**退出**tab 键顺序**模式。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)