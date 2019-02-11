---
title: 更改或删除未赋值的符号
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.unassigned
helpviewer_keywords:
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
ms.assetid: b6abee4a-3c24-4697-a166-fe6a86cad35f
ms.openlocfilehash: 47cc3d7a387092afe77fdbcf4bbdb6d085eeda25
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987009"
---
# <a name="changing-or-deleting-unassigned-symbols"></a>更改或删除未赋值的符号

在处于[资源符号对话框](../windows/resource-symbols-dialog-box.md)，可以编辑或删除现有不已分配给资源或对象的符号。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

## <a name="to-change-an-unassigned-symbol"></a>更改未分配的符号

1. 在中**名称**框中，选择未分配的符号，然后选择**更改**。

1. 中提供的框中编辑符号的名称或值**更改符号**对话框。

   > [!NOTE]
   > 若要更改符号的*是*分配给资源或对象，必须使用资源编辑器或**属性**窗口。 有关详细信息，请参阅[更改符号或符号名](../windows/changing-a-symbol-or-symbol-name-id.md)。

## <a name="to-delete-an-unassigned-unused-symbol"></a>删除未分配（未使用）的符号

在中[资源符号对话框](../windows/resource-symbols-dialog-box.md)，选择你想要删除，并且选择符号**删除**。

   > [!NOTE]
   > 在资源文件中删除未使用的符号之前，请确保它未在程序中的其他位置使用，也未由编译时包含的资源文件使用。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[查看资源符号](../windows/viewing-resource-symbols.md)<br/>
[符号名限制](../windows/symbol-name-restrictions.md)<br/>
[符号值限制](../windows/symbol-value-restrictions.md)<br/>
[预定义的符号 ID](../windows/predefined-symbol-ids.md)