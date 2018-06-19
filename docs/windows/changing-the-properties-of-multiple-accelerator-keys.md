---
title: 更改多个快捷键属性 |Microsoft 文档
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
ms.openlocfilehash: 11705fcbcdb3dc73fe5c3a87844b2bc5d90cd135
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33913013"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys"></a>更改多个快捷键的属性
### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>若要更改的多个快捷键属性  
  
1.  通过双击图标中的将其打开的快捷键对应表[资源视图](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  选择你想要更改按下的快捷键**CTRL**单击每个键。  
  
3.  转到[属性窗口](/visualstudio/ide/reference/properties-window)和中所需所有选择的快捷键共享的值的类型。  
  
    > [!NOTE]
    >  每个修饰符值显示为属性窗口中的布尔属性。 如果你更改[修饰符](../windows/accelerator-modifier-property.md)属性窗口的快捷键对应表中的值将视为对先前已存在任何修饰符的附加新的修饰符。 因此，如果你设置任何修饰符值，你将需要将它们以确保每个快捷键共享相同的修饰符设置所有设置。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [编辑快捷键对应表](../windows/editing-accelerator-tables.md)   
 [快捷键编辑器](../windows/accelerator-editor.md)