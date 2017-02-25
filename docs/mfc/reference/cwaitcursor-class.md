---
title: "CWaitCursor Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWaitCursor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "光标, wait cursor"
  - "CWaitCursor class"
  - "wait cursors"
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CWaitCursor Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供一行显示方式等待光标，通常显示为一个沙漏，而您执行较长操作。  
  
## 语法  
  
```  
class CWaitCursor  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWaitCursor::CWaitCursor](../Topic/CWaitCursor::CWaitCursor.md)|构造 `CWaitCursor` 对象并显示等待光标。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWaitCursor::Restore](../Topic/CWaitCursor::Restore.md)|在更改后，回收等待光标它。|  
  
## 备注  
 `CWaitCursor` 没有基类。  
  
 编程做法的好Windows需要公开等待光标时，都将执行需要很长时间的操作。  
  
 若要显示等待光标，请在执行较长操作的代码之前定义一个 `CWaitCursor` 变量。  对象的构造函数自动导致等待光标显示。  
  
 当对象超出范围\(在 `CWaitCursor` 对象声明\)的块的末尾，此析构函数中设置光标到以前的光标。  换言之，对象会自动执行必要的清理。  
  
> [!NOTE]
>  由于其构造函数和析构函数如何工作，`CWaitCursor` 对象始终声明为局部变量\-\-它们不声明为全局变量也不是它们分配了 **new**。  
  
 如果执行可能游标已更改，例如显示消息框或对话框的操作，请调用 [还原](../Topic/CWaitCursor::Restore.md) 成员函数继续等待光标。  即使等待光标当前显示，可以调用 **Restore**。  
  
 （另一种显示等待光标将使用 [CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)、 [CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)和 [CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)的组合。  但是，`CWaitCursor` 更易于使用，因为您无需设置光标到以前的光标，当处理较长操作时。  
  
> [!NOTE]
>  使用 [CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md) 虚函数，MFC设置和还原光标。  可以重写此函数提供自定义行为。  
  
## 继承层次结构  
 `CWaitCursor`  
  
## 要求  
 **标头：**afxwin.h  
  
## 示例  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/CPP/cwaitcursor-class_1.cpp)]  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)   
 [CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)   
 [CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)   
 [CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md)   
 [如何:我更改在Microsoft基础类选件应用程序的鼠标光标?](http://go.microsoft.com/fwlink/?LinkID=128044)