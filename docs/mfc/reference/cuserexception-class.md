---
title: "CUserException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserException class"
  - "错误 [C++], 捕获"
  - "异常, 引发"
  - "operations [C++]"
  - "operations [C++], stopping"
  - "引发异常, stopping user operations"
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CUserException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引发终止最终用户操作。  
  
## 语法  
  
```  
class CUserException : public CSimpleException  
```  
  
## 备注  
 如果要为特定的异常时，使用引发或捕获异常框架使用 `CUserException`。"  用户”类名的可被解释“我的用户执行我需要处理异常的操作”。  
  
 `CUserException` 在调用全局函数后 `AfxMessageBox` 通知用户就会引发操作失败。  当您编写异常处理程序，处理特殊的异常，因为用户已经通常是通知该失败。  框架在某些情况下引发此异常。  引发 `CUserException`，提醒用户然后调用全局函数 `AfxThrowUserException`。  
  
 在下面的示例中，包含可能失败用户报警并引发 `CUserException`操作的功能。  调用函数专门捕获异常并处理它:  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/CPP/cuserexception-class_1.cpp)]  
  
 有关使用 `CUserException`的更多信息，请参见文章 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [AfxMessageBox](../Topic/AfxMessageBox.md)   
 [AfxThrowUserException](../Topic/AfxThrowUserException.md)   
 [如何:我创建"我的自定义异常选件类?](http://go.microsoft.com/fwlink/?LinkId=128045)