---
title: "COleDispatchException Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDispatchException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动化, 异常"
  - "COleDispatchException class"
  - "异常, OLE"
  - "OLE exceptions, to IDispatch interface"
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDispatchException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

处理异常特定于OLE `IDispatch` 接口，必须是OLE自动化的重要组成部分。  
  
## 语法  
  
```  
class COleDispatchException : public CException  
```  
  
## 成员  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleDispatchException::m\_dwHelpContext](../Topic/COleDispatchException::m_dwHelpContext.md)|错误的帮助上下文。|  
|[COleDispatchException::m\_strDescription](../Topic/COleDispatchException::m_strDescription.md)|口头错误说明。|  
|[COleDispatchException::m\_strHelpFile](../Topic/COleDispatchException::m_strHelpFile.md)|使用的帮助文件与 `m_dwHelpContext`。|  
|[COleDispatchException::m\_strSource](../Topic/COleDispatchException::m_strSource.md)|生成异常的应用程序。|  
|[COleDispatchException::m\_wCode](../Topic/COleDispatchException::m_wCode.md)|`IDispatch`特定的错误代码。|  
  
## 备注  
 与 `CException` 基类派生的其他异常选件类，`COleDispatchException` 可用于 **THROW**、 `THROW_LAST`、 **TRY**、 **"CATCH"**、 `AND_CATCH`和 `END_CATCH` 宏。  
  
 通常，应调用 [AfxThrowOleDispatchException](../Topic/AfxThrowOleDispatchException.md) 创建并引发 `COleDispatchException` 对象。  
  
 有关异常的更多信息，请参见位于 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [异常:OLE异常](../../mfc/exceptions-ole-exceptions.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [MFC示例CALCDRIV](../../top/visual-cpp-samples.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDispatchDriver Class](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException Class](../../mfc/reference/coleexception-class.md)