---
title: "添加事件向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.event.overview
dev_langs: C++
helpviewer_keywords: Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 62ecbe7dece323ce5e99fbe32b3b936fe3661362
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="add-event-wizard"></a>添加事件向导
此向导将事件添加到 MFC ActiveX 控件项目。 你可以指定自己的事件，你可以自定义的通常常用事件，或可以从常用事件的列表中选择。  
  
 **事件名称**  
 设置自动化客户端用于从类请求事件的名称。 输入的名称或从列表中选择一个。  
  
 **事件类型**  
 指示要添加事件的类型。 仅当选择从可用**事件名称**列表。  
  
|选项|描述|  
|------------|-----------------|  
|**常用**|指定将此类实现的常用事件，例如单击按钮;。 常用事件是在 Microsoft 基础类 (MFC) 库中定义的。|  
|**自定义**|指定你要提供您自己的事件的实现。|  
  
 **内部名称**  
 设置成员函数将事件发送的文件的名称。 仅适用于自定义事件。 名称基于**事件名称**。 如果你想要提供一个名称不同，你可以更改该内部名称**事件名称**。  
  
 **参数类型**  
 设置的类型**参数名称**。 从列表中选择类型。  
  
 **参数名称**  
 设置用于通过事件传递的参数的名称。 键入名称后，你必须单击**添加**以将其添加参数的列表。  
  
 单击后**添加**，参数名称将显示在**参数列表**。  
  
> [!NOTE]
>  如果你提供参数名称，然后单击**完成**在单击之前**添加**，则不会将参数添加到事件。 你必须找到方法，并手动将参数插入。 **参数列表**  
  
 **添加**  
 添加你在中指定的参数**参数名称**，及其类型到**参数列表**。 你必须单击**添加**将参数添加到列表。  
  
 **移除**  
 中移除在中选择的参数**参数列表**从列表中。  
  
 **参数列表**  
 显示所有参数和参数类型当前为该方法添加的。 添加参数时，向导将更新**参数列表**以显示其类型的每个参数。  
  
## <a name="see-also"></a>请参阅  
 [添加事件](../ide/adding-an-event-visual-cpp.md)