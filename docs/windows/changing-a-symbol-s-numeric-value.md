---
title: 更改符号&#39;s 数值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 748b45b93f6145a03d8cd9745b7b61e3482ec53d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603739"
---
# <a name="changing-a-symbol39s-numeric-value"></a>更改符号&#39;s 数值

对于与单个资源相关联的符号，可以使用[属性窗口](/visualstudio/ide/reference/properties-window)若要更改符号值。 可以使用[资源符号对话框](../windows/resource-symbols-dialog-box.md)若要更改的当前未分配给资源的符号的值。 有关详细信息，请参阅[更改未赋值符号](../windows/changing-unassigned-symbols.md)。

### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>更改分配给单个资源或对象的符号值

1. 在中[资源视图](../windows/resource-view-window.md)，选择的资源。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在中**属性**窗口中，键入符号名称后跟一个等号和中的整数**ID**框中，例如：

    ```
    IDC_EDITNAME=5100
    ```

下次保存项目时，新值会存储在符号头文件中。 只有符号名在 ID 框中保持可见；等号和值在进行验证之后不会显示。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息以及 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[符号值限制](../windows/symbol-value-restrictions.md)  
[预定义的符号 ID](../windows/predefined-symbol-ids.md)