---
title: 删除版本信息块 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
ms.assetid: 4e1641eb-d5b2-4183-b273-bc5b51af1537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6951904f0a579017c5a5a76f7fd8ba798017a34b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425049"
---
# <a name="deleting-a-version-information-block-c"></a>删除版本信息块 （c + +）

### <a name="to-delete-a-version-information-block"></a>删除版本信息块

1. 通过在 [资源视图](../windows/resource-view-window.md)中双击图标来打开版本信息资源。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 右键单击想要删除的块标头，然后从快捷菜单中选择“删除版本信息块”  。

   此命令会删除所选标头，并使其余的版本信息保持不变。 请注意此操作不能撤消。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[版本信息编辑器](../windows/version-information-editor.md)<br/>
[版本信息 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)