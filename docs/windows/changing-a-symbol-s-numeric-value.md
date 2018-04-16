---
title: "更改符号 &#39; s 数字值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce2c846d844b79a6ff054bb6c209d1f4653a26d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="changing-a-symbol39s-numeric-value"></a>更改符号 &#39; s 数字值
对于与单个资源关联的符号，你可以使用[属性窗口](/visualstudio/ide/reference/properties-window)更改符号值。 你可以使用[资源符号对话框](../windows/resource-symbols-dialog-box.md)若要更改的当前未分配给资源的符号的值。 有关详细信息，请参阅[更改未分配的符号](../windows/changing-unassigned-symbols.md)。  
  
### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>更改分配给单个资源或对象的符号值  
  
1.  在[资源视图](../windows/resource-view-window.md)，选择资源。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**属性**窗口中，键入符号名称后面跟一个等号和内的整数**ID**框中，例如：  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 下次保存项目时，新值会存储在符号头文件中。 只有符号名在 ID 框中保持可见；等号和值在进行验证之后不会显示。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息以及 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 惠?  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [符号值限制](../windows/symbol-value-restrictions.md)   
 [预定义的符号 ID](../windows/predefined-symbol-ids.md)