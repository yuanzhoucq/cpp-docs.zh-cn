---
title: 创建新符号 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- symbols, creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d1911a8bd8a7f3079497ec66ea1de59aff480a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604045"
---
# <a name="creating-new-symbols"></a>创建新符号

开始新项目时，你可能会发现在创建将所需符号名分配给的资源之前标出这些名称会十分方便。

### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>使用资源符号对话框创建新符号

1. 在中[资源符号对话框](../windows/resource-symbols-dialog-box.md)，选择**新建**。

2. 在中**名称**框中，键入符号名称。

3. 接受分配的符号值。

   或

   在中**值**框中，键入新值。

4. 单击**确定**将新符号添加到符号列表。

如果输入的符号名已存在，则会出现一个消息框，表明已定义具有该名称的符号。 无法定义具有相同名称的两个或多个符号，但是可以定义具有相同数值的不同符号。 有关详细信息，请参阅[符号名限制](../windows/symbol-name-restrictions.md)并[符号值限制](../windows/symbol-value-restrictions.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息以及 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[查看资源符号](../windows/viewing-resource-symbols.md)  
[预定义的符号 ID](../windows/predefined-symbol-ids.md)