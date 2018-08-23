---
title: 更改符号或符号名 (ID) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2fb5268ca23def96c31f724b93fbdf1c81c4a43
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599690"
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>更改符号或符号名 (ID)

创建新资源或资源对象时，开发环境会向它分配默认符号名，例如 IDD_DIALOG1。 可以使用[属性窗口](/visualstudio/ide/reference/properties-window)更改默认符号名或更改任何已与资源关联的符号的名称。

### <a name="to-change-a-resources-symbol-name"></a>更改资源的符号名

1. 在中[资源视图](../windows/resource-view-window.md)，选择的资源。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在中**属性**窗口中，输入新符号名或从现有符号列表中选择**ID**框。

   如果输入新符号名，则会自动向它赋值。

可以使用[资源符号对话框](../windows/resource-symbols-dialog-box.md)更改当前未分配给资源的符号的名称。 有关详细信息，请参阅[更改未赋值符号](../windows/changing-unassigned-symbols.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[符号名限制](../windows/symbol-name-restrictions.md)  
[预定义的符号 ID](../windows/predefined-symbol-ids.md)