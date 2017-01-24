---
title: "PAINTSTRUCT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PAINTSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PAINTSTRUCT 结构"
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# PAINTSTRUCT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`PAINTSTRUCT` 结构包含可用于绘制窗口的工作区的信息。  
  
## 语法  
  
```  
  
      typedef struct tagPAINTSTRUCT {  
   HDC hdc;  
   BOOL fErase;  
   RECT rcPaint;  
   BOOL fRestore;  
   BOOL fIncUpdate;  
   BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### 参数  
 *hdc*  
 标识为绘制将显示使用的上下文。  
  
 *fErase*  
 指定背景是否需要重新绘制。  如果应用程序应当绘制背景，则不是 0。  应用程序负责绘制后台运行，如果 Windows 窗口类创建，而后台画笔 \(参见 [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) 结构的 **hbrBackground** 成员在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]中的说明\)。  
  
 *rcPaint*  
 请求指定绘制矩形的左上角和右下角。  
  
 *fRestore*  
 reserve 成员 \[STL\/CLR\]  窗口内部使用。  
  
 *fIncUpdate*  
 reserve 成员 \[STL\/CLR\]  窗口内部使用。  
  
 *rgbReserved\[16\]*  
 reserve 成员 \[STL\/CLR\]  窗口内部使用的保留的内存块。  
  
## 要求  
 **头文件：** winuser.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m\_ps](../Topic/CPaintDC::m_ps.md)