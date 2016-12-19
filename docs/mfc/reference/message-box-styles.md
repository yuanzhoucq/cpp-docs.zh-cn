---
title: "消息框样式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MB_ICONQUESTION"
  - "MB_ICONINFORMATION"
  - "MB_DEFBUTTON2"
  - "MB_YESNO"
  - "MB_OKCANCEL"
  - "MB_TASKMODAL"
  - "MB_ICONEXCLAMATION"
  - "MB_OK"
  - "MB_DEFBUTTON3"
  - "MB_YESNOCANCEL"
  - "MB_APPLMODAL"
  - "MB_RETRYCANCEL"
  - "MB_DEFBUTTON1"
  - "MB_ABORTRETRYIGNORE"
  - "MB_SYSTEMMODAL"
  - "MB_ICONSTOP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MB_ABORTRETRYIGNORE 常量"
  - "MB_APPLMODAL 常量"
  - "MB_DEFBUTTON1 常量"
  - "MB_DEFBUTTON2 常量"
  - "MB_DEFBUTTON3 常量"
  - "MB_ICONEXCLAMATION 常量"
  - "MB_ICONINFORMATION 常量"
  - "MB_ICONQUESTION 常量"
  - "MB_ICONSTOP 常量"
  - "MB_OK 常量"
  - "MB_OKCANCEL 常量"
  - "MB_RETRYCANCEL 常量"
  - "MB_SYSTEMMODAL 常量"
  - "MB_TASKMODAL 常量"
  - "MB_YESNO 常量"
  - "MB_YESNOCANCEL 常量"
  - "消息框样式"
ms.assetid: d87014c5-4ea4-4950-a27e-7bcdda67be7d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息框样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的样式提供。  
  
## Message\_Box 类型  
  
-   **MB\_ABORTRETRYIGNORE** 消息框包含三个按钮：中止，重试和忽略。  
  
-   **MB\_OK** 消息框包含一个按钮：好。  
  
-   **MB\_OKCANCEL** 消息框包含两个按钮：好和取消。  
  
-   **MB\_RETRYCANCEL** 消息框包含两个按钮：重试和取消。  
  
-   **MB\_YESNO** 消息框包含两个按钮：Yes 和 No。  
  
-   **MB\_YESNOCANCEL** 消息框包含三个按钮：是，而和取消。  
  
## 窗体消息框  
  
-   用户必须响应消息在继续在当前窗口的工作之前的 **MB\_APPLMODAL**。  但是，用户可以在这些窗口可以移到其他 Windows 应用程序和工作。  **MB\_SYSTEMMODAL**，则 **MB\_TASKMODAL** 和不指定，则默认值为 **MB\_APPLMODAL**。  
  
-   所有**MB\_SYSTEMMODAL** 应用程序挂起，直至用户响应消息框。  系统模式消息框用于通知需要立即考虑，应慎重使用很大，可能有害的用户。  
  
-   **MB\_TASKMODAL** 与 **MB\_APPLMODAL**，有用，但不在 Microsoft 基础类 \(MFC\) 应用程序中。  此标志为没有可用的窗口句柄的调用应用程序或库是保留的。  
  
## 消息框图标  
  
-   感叹号**MB\_ICONEXCLAMATION** 图标出现消息框。  
  
-   **MB\_ICONINFORMATION** 包括图标“i”的圆形显示消息框。  
  
-   **MB\_ICONQUESTION** 在消息框中显示问号图标  
  
-   **MB\_ICONSTOP** 停止符号图标出现消息框。  
  
## 默认消息框按钮  
  
-   **MB\_DEFBUTTON1** 第一个是默认按钮。  注意第一次按钮始终是默认，除非指定 **MB\_DEFBUTTON2** 或 **MB\_DEFBUTTON3**。  
  
-   **MB\_DEFBUTTON2** 第二个按钮是默认设置。  
  
-   **MB\_DEFBUTTON3** 是默认第三个按钮。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)   
 [AfxMessageBox](../Topic/AfxMessageBox.md)