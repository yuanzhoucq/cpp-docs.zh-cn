---
title: 移动或快捷键对应表项复制到另一个资源脚本文件 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
ms.assetid: 7b4dc149-c972-4ab2-8477-76c52b6feb5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d3f75ef8c2820c227716e3208ff2cded54d1fd7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414727"
---
# <a name="moving-or-copying-an-accelerator-table-entry-to-another-resource-script-file-c"></a>移动或复制到另一个资源脚本文件 （c + +） 的快捷键对应表项

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>将快捷键对应表项移动或复制到另一个资源脚本文件

1. 在这两个资源脚本文件中打开快捷键对应表。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 选择要移动的项。

3. 从**编辑**菜单中，选择**副本**或**剪切**。

4. 在目标资源脚本文件中选择一个项。

5. 从**编辑**菜单中，选择**粘贴**。

   > [!NOTE]
   > 还可以使用快捷键进行复制和粘贴。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[编辑快捷键对应表](../windows/editing-accelerator-tables.md)<br/>
[快捷键编辑器](../windows/accelerator-editor.md)