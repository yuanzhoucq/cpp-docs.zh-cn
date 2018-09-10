---
title: 从快捷键对应表 （c + +） 删除项 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
ms.assetid: cc9cd499-dc04-4fe6-9393-a3e471e115a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 747e0db32a73a277ef26e18e787e3e5a31f69578
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315114"
---
# <a name="deleting-an-entry-from-an-accelerator-table-c"></a>从快捷键对应表 （c + +） 删除项

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>若要从快捷键对应表删除项

1. 通过双击中对应的图标打开快捷键对应表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 选择要删除的项。 (按住**Ctrl**或**Shift**键同时单击选择多个条目。)

3. 右键单击并选择**删除**从快捷菜单 (或选择**删除**从**编辑**菜单)。

\- 或 -

- 按**删除**密钥。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[编辑快捷键对应表](../windows/editing-accelerator-tables.md)  
[快捷键编辑器](../windows/accelerator-editor.md)