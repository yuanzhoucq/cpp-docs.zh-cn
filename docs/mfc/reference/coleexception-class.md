---
title: "COleException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleException class"
  - "异常, OLE"
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示异常条件与OLE操作相关。  
  
## 语法  
  
```  
class COleException : public CException  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleException::Process](../Topic/COleException::Process.md)|将所捕获的异常为OLE返回代码。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleException::m\_sc](../Topic/COleException::m_sc.md)|包含指示异常原因的状态代码。|  
  
## 备注  
 `COleException` 选件类包括保存指示异常的状态代码导致的一个公共数据成员。  
  
 一般而言，不应直接创建 `COleException` 对象;相反，应调用 [AfxThrowOleException](../Topic/AfxThrowOleException.md)。  
  
 有关异常的更多信息，请参见位于 [异常处理\(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [异常:OLE异常](../../mfc/exceptions-ole-exceptions.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [MFC示例CALCDRIV](../../top/visual-cpp-samples.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)