---
title: 编辑 ActiveX 控件的属性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e5880c62-36c7-4701-bc99-97a82974c22a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e754307c35d10aa36680a42415bd3a5b781321ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384840"
---
# <a name="editing-properties-for-an-activex-control"></a>编辑 ActiveX 控件的属性

提供独立供应商的 ActiveX 控件可能都配备有其自己的属性和特征。 ActiveX 控件的属性显示在**属性**窗口。 此外，创建 ActiveX 控件的编写器的任何属性页中显示**属性页**对话框中 (若要查看**属性页**特定的 ActiveX 控件，请单击**属性页**按钮[属性窗口](/visualstudio/ide/reference/properties-window))。

ActiveX 控件，具体取决于为 ActiveX 控件的一部分的属性表的属性页中显示各个选项卡。

> [!NOTE]
> 以下过程适用于使用属性页编辑 ActiveX 控件。 此外可以浏览，并在新编辑 ActiveX 属性**属性**窗口。

### <a name="to-edit-properties-for-an-activex-control"></a>若要编辑的 ActiveX 控件的属性

1. 选择**ActiveX**控件。

2. 上**视图**菜单上，单击**属性页**并查看属性。

3. 根据需要在属性页中进行更改。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[查看 ActiveX 控件并将其添加到对话框](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[对话框中的控件](../windows/controls-in-dialog-boxes.md)<br/>
[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[ActiveX 控件容器](../mfc/activex-control-containers.md)