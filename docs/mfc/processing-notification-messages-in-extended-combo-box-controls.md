---
title: "处理中的通知消息扩展组合框控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a78e7b9fd8f9c67f14a4bb51088866785d372cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>处理扩展组合框控件中的通知消息
当用户与扩展组合框进行交互时，控件 (`CComboBoxEx`) 会将通知消息发送到其父窗口（通常是一个视图或对话框对象）。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户激活下拉列表或单击该控件的编辑框时，将发送 **CBEN_BEGINEDIT** 通知。  
  
 请使用“属性”窗口将通知处理程序添加到你希望实现的那些消息的父类。  
  
 下表介绍了由扩展组合框控件发送的各种通知。  
  
-   **CBEN_BEGINEDIT** 用户激活下拉列表或单击该控件的编辑框时发送。  
  
-   **CBEN_DELETEITEM** 删除某项时发送。  
  
-   **CBEN_DRAGBEGIN** 用户开始拖动控件编辑部分中显示的项图片时发送。  
  
-   **CBEN_ENDEDIT** 用户结束编辑框中的某个操作或从控件的下拉列表中选择某个项后发送。  
  
-   **CBEN_GETDISPINFO** 要检索有关回调项的显示信息时发送。  
  
-   **CBEN_INSERTITEM** 在控件中插入新项后发送。  
  
## <a name="see-also"></a>请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)

