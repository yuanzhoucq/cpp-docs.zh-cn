---
title: "处理扩展组合框控件中的通知消息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "扩展组合框, 通知"
  - "通知, 扩展组合框控件"
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理扩展组合框控件中的通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户与扩展组合框进行交互时，控件 \(`CComboBoxEx`\) 会将通知消息发送到其父窗口（通常是一个视图或对话框对象）。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户激活下拉列表或单击该控件的编辑框时，将发送 **CBEN\_BEGINEDIT** 通知。  
  
 请使用“属性”窗口将通知处理程序添加到你希望实现的那些消息的父类。  
  
 下表介绍了由扩展组合框控件发送的各种通知。  
  
-   **CBEN\_BEGINEDIT** 用户激活下拉列表或单击该控件的编辑框时发送。  
  
-   **CBEN\_DELETEITEM** 删除某项时发送。  
  
-   **CBEN\_DRAGBEGIN** 用户开始拖动控件编辑部分中显示的项图片时发送。  
  
-   **CBEN\_ENDEDIT** 用户结束编辑框中的某个操作或从控件的下拉列表中选择某个项后发送。  
  
-   **CBEN\_GETDISPINFO** 要检索有关回调项的显示信息时发送。  
  
-   **CBEN\_INSERTITEM** 在控件中插入新项后发送。  
  
## 请参阅  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控件](../mfc/controls-mfc.md)