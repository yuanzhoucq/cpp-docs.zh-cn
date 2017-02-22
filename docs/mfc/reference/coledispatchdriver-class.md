---
title: "COleDispatchDriver Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDispatchDriver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation clients, implementing Automation"
  - "COleDispatchDriver class"
  - "OLE dispatch interface"
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleDispatchDriver Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现OLE自动化客户端。  
  
## 语法  
  
```  
class COleDispatchDriver  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDispatchDriver::COleDispatchDriver](../Topic/COleDispatchDriver::COleDispatchDriver.md)|构造 `COleDispatchDriver` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDispatchDriver::AttachDispatch](../Topic/COleDispatchDriver::AttachDispatch.md)|将一个与 `COleDispatchDriver` 对象的 `IDispatch` 连接。|  
|[COleDispatchDriver::CreateDispatch](../Topic/COleDispatchDriver::CreateDispatch.md)|创建 `IDispatch` 连接并附加到 `COleDispatchDriver` 对象。|  
|[COleDispatchDriver::DetachDispatch](../Topic/COleDispatchDriver::DetachDispatch.md)|分离 `IDispatch` 连接，而无需将其释放。|  
|[COleDispatchDriver::GetProperty](../Topic/COleDispatchDriver::GetProperty.md)|获取自动化属性。|  
|[COleDispatchDriver::InvokeHelper](../Topic/COleDispatchDriver::InvokeHelper.md)|调用的自动化方法帮助器。|  
|[COleDispatchDriver::ReleaseDispatch](../Topic/COleDispatchDriver::ReleaseDispatch.md)|释放 `IDispatch` 连接。|  
|[COleDispatchDriver::SetProperty](../Topic/COleDispatchDriver::SetProperty.md)|设置自动化属性。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[COleDispatchDriver::operator \=](../Topic/COleDispatchDriver::operator%20=.md)|复制源值。`COleDispatchDriver` 对象。|  
|[COleDispatchDriver::operator LPDISPATCH](../Topic/COleDispatchDriver::operator%20LPDISPATCH.md)|访问基础 `IDispatch` 指针。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleDispatchDriver::m\_bAutoRelease](../Topic/COleDispatchDriver::m_bAutoRelease.md)|指定是否在 `ReleaseDispatch` 或对象销毁时释放 `IDispatch`。|  
|[COleDispatchDriver::m\_lpDispatch](../Topic/COleDispatchDriver::m_lpDispatch.md)|指示指向 `IDispatch` 接口附加到此 `COleDispatchDriver`。|  
  
## 备注  
 `COleDispatchDriver` 没有基类。  
  
 OLE调度接口提供对对象的方法和属性。  `COleDispatchDriver` 的成员函数附加属性，分离，创建，并释放类型 `IDispatch`的计划连接。  其他成员函数使用变量参数列表简化 **IDispatch::Invoke**。  
  
 可以直接使用此选件类，但是，添加选件类向导创建的选件类通常只使用它。  在创建时新的C\+\+通过导入类型类库，新选件类从 `COleDispatchDriver`派生。  
  
 有关使用 `COleDispatchDriver`的更多信息，请参见以下文章:  
  
-   [自动化客户端](../../mfc/automation-clients.md)  
  
-   [自动化服务器](../../mfc/automation-servers.md)  
  
## 继承层次结构  
 `COleDispatchDriver`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [MFC示例CALCDRIV](../../top/visual-cpp-samples.md)   
 [MFC示例ACDUAL](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)