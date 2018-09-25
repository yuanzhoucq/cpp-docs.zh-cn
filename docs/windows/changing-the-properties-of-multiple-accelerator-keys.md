---
title: 更改属性的多个快捷键 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 56deca345915c5736cb15e7ce5d8d0e0ee0b7062
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400779"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>更改属性的多个快捷键 （c + +）

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要更改多个快捷键的属性

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 选择你想要更改通过按下的快捷键**Ctrl**单击每个键。

3. 转到[属性窗口](/visualstudio/ide/reference/properties-window)和中所需的所选的加速器共享所有的值类型。

   > [!NOTE]
   > 每个修饰符值显示为一个布尔值属性中**属性**窗口。 如果您更改[修饰符](../windows/accelerator-modifier-property.md)中的值**属性**窗口中，快捷键对应表视为新修饰符对先前已存在任何修饰符的补充。 因此，如果设置任何修饰符的值，您将需要设置它们以确保每个快捷键共享相同的所有**修饰符**设置。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[编辑快捷键对应表](../windows/editing-accelerator-tables.md)<br/>
[快捷键编辑器](../windows/accelerator-editor.md)