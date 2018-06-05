---
title: 添加事件向导 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.event.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f92f871f22fb01f3f0f37677c393fcd481c08120
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325190"
---
# <a name="add-event-wizard"></a>添加事件向导
此向导将事件添加到 MFC ActiveX 控件项目。 可以指定自己的事件，自定义典型的常用事件，或者从常用事件列表中进行选择。  
  
 **事件名称**  
 设置自动化客户端用来从该类中请求事件的名称。 请输入名称或从列表中选择一个。  
  
 **事件类型**  
 指示要添加的事件类型。 仅当从“事件名称”列表中选择时才可用。  
  
|选项|描述|  
|------------|-----------------|  
|**常用**|指定将对此类实现的常用事件，例如单击按钮。 在 Microsoft 基础类 (MFC) 库中指定常用事件。|  
|**自定义**|指定你要提供的自己的事件实现。|  
  
 **内部名称**  
 设置发送该事件的成员函数的名称。 仅适用于自定义事件。 此名称基于“事件名称”。 如果想提供不同于“事件名称”的名称，也可以更改内部名称。  
  
 **参数类型**  
 设置“参数名称”的类型。 从列表中选择类型。  
  
 **参数名称**  
 设置要通过事件传递的参数名称。 键入名称后，必须单击“添加”才能将其添加到参数列表中。  
  
 单击“添加”后，参数名称随即显示在“参数列表”中。  
  
> [!NOTE]
>  如果提供参数名称，然后在单击“添加”前先单击“完成”，则不会将该参数添加到事件中。 必须找到该方法并手动插入参数。 **参数列表**  
  
 **添加**  
 将在“参数名称”及其类型中指定的参数添加到“参数列表”。 必须单击“添加”才能将参数添加到列表中。  
  
 **移除**  
 从列表中删除在“参数列表”中选择的参数。  
  
 **参数列表**  
 显示当前为该方法添加的所有参数及其类型。 添加参数时，向导更新“参数列表”以显示每个参数及其类型。  
  
## <a name="see-also"></a>请参阅  
 [添加事件](../ide/adding-an-event-visual-cpp.md)