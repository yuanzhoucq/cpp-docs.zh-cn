---
title: 添加或删除字符串资源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c22990c504700ab82ae0d7542420a3f82db4d73
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314035"
---
# <a name="adding-or-deleting-a-string-resource-c"></a>添加或删除字符串资源 （c + +）

可快速插入到字符串表使用的新条目**字符串**编辑器。 新字符串放在表的末尾，并将给定的下一步提供标识符。 然后，你可以编辑**ID**，**值**，或**标题**中的属性[属性窗口](/visualstudio/ide/reference/properties-window)根据需要。

**字符串**编辑器可确保不使用已在使用的 ID。 如果您选择 ID 已在使用中，**字符串**编辑器将通知你，然后分配一个通用的唯一 ID，例如`IDS_STRING58113`。

### <a name="to-add-a-string-table-entry"></a>若要添加的字符串表项

1. 通过双击中对应的图标打开字符串表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 字符串表中右键单击并选择**新的字符串**从快捷菜单。

3. 在中**字符串**编辑器中，选择**ID**从 ID 下拉列表或类型 ID 直接在位置。

4. 编辑**值**，如果有必要。

5. 键入的条目**标题**。

   > [!NOTE]
   > 在 Windows 字符串表中不允许 null 字符串。 如果在是一个 null 字符串的字符串表中创建一个条目，您将收到一条消息询问你为"请输入一个字符串，此表项。"

### <a name="to-delete-a-string-table-entry"></a>若要删除的字符串表项

1. 选择要删除的项。

2. 上**编辑**菜单上，单击**删除**。

\- 或 -

- 右键单击你想要删除选择的字符串**删除**从快捷菜单。

\- 或 -

- 按**删除**密钥。

有关将资源添加到托管项目 （项目面向公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： 本地化 Windows 窗体](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\))。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[字符串编辑器](../windows/string-editor.md)  