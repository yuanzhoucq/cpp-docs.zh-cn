---
title: 定义助记键 （访问键） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d707b0205c3f13954681eb4f6a033496a2997ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425783"
---
# <a name="defining-mnemonics-access-keys"></a>定义助记键（访问键）

通常情况下，键盘用户输入的焦点从一个控件移动到另一个中使用的对话框**选项卡**并**箭头**密钥。 但是，可以定义允许用户通过按一个键选择一个控件的访问键 （助记键或容易记忆的名称）。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定义具有可见标题 （下压按钮、 复选框和单选按钮） 的控件的访问键

1. 选择对话框的上的控件。

2. 中[属性窗口](/visualstudio/ide/reference/properties-window)，在**标题**属性中，键入新名称进行控制，键入 & 符 (`&`) 要将该控件的访问密钥作为字母前。 例如 `&Radio1`。

3. 按 **Enter**。

   在显示的标题以指示访问密钥，例如，会出现下划线**R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定义没有可见标题的控件的访问键

1. 通过使用使控件的标题**静态文本**控制[工具箱](/visualstudio/ide/reference/toolbox)。

2. 在静态文本标题中，输入与号 (`&`) 所需的访问密钥作为字母前。

3. 请确保静态文本控件紧跟其 tab 键顺序标记的控件。

对话框中的所有访问键应都是唯一的。

### <a name="to-check-for-duplicate-access-keys"></a>若要检查重复的访问键

1. 上**格式**菜单上，单击**检查助记键**。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[控件](../mfc/controls-mfc.md)