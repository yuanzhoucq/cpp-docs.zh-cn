---
title: "使用 CAnimateCtrl | Microsoft Docs"
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
  - "CAnimateCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "动画控件 [C++], CAnimateCtrl 类"
  - "CAnimateCtrl 类, 关于 CAnimateCtrl 类"
  - "控件 [MFC], 动画"
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CAnimateCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

动画控件，由 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)类，是查看音频视频交错 \(AVI\) 格式的 \- 标准窗口\/音频剪辑视频的格式。  AVI 剪辑是一系列位图帧，如脚本。  
  
 由于线程继续执行时，剪裁 AVI 时，一个常见用途对控件是指示系统活动在较长操作时。  例如，窗口查找对话框显示一个放大镜移动为文件的系统。  
  
 控件仅能简单的动画播放 AVI 剪辑，并且，它们不支持声音。有关限制的完整列表，请参见[CAnimateCtrl](../mfc/reference/canimatectrl-class.md) 。因为对控件的功能有严重限制和发生更改，则应使用备用 MCIWnd 如控件，则需要控件提供对多媒体播放和记录功能。  有关 MCIWnd 控件的更多信息，请参见文档。多媒体  
  
## 您想进一步了解什么？  
  
-   [使用动画控件](../mfc/using-an-animation-control.md)  
  
-   [动画控件发送的通知](../mfc/notifications-sent-by-animation-controls.md)  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)