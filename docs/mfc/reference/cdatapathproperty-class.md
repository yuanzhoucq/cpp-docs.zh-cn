---
title: "CDataPathProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDataPathProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 异步"
  - "asynchronous controls [C++]"
  - "CDataPathProperty class"
  - "OLE 控件 [C++], 异步"
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDataPathProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现可加载异步的一个OLE控件属性。  
  
## 语法  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDataPathProperty::CDataPathProperty](../Topic/CDataPathProperty::CDataPathProperty.md)|构造 `CDataPathProperty` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDataPathProperty::GetControl](../Topic/CDataPathProperty::GetControl.md)|检索异步OLE控件与 `CDataPathProperty` 对象。|  
|[CDataPathProperty::GetPath](../Topic/CDataPathProperty::GetPath.md)|检索属性的路径名。|  
|[CDataPathProperty::Open](../Topic/CDataPathProperty::Open.md)|启动异步属性的加载关联的ActiveX \(OLE\)控件的。|  
|[CDataPathProperty::ResetData](../Topic/CDataPathProperty::ResetData.md)|调用 `CAsyncMonikerFile::OnDataAvailable` 通知容器控件属性已更改。|  
|[CDataPathProperty::SetControl](../Topic/CDataPathProperty::SetControl.md)|设置异步ActiveX \(OLE\)控件与属性。|  
|[CDataPathProperty::SetPath](../Topic/CDataPathProperty::SetPath.md)|设置属性的路径名。|  
  
## 备注  
 异步属性在同步启动后加载。  
  
 选件类 `CDataPathProperty` 从 **CAysncMonikerFile**派生。  若要实现在您的OLE控件的异步特性，从 `CDataPathProperty`派生选件类，并重写 [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md)。  
  
 有关如何使用异步标记和ActiveX控件的更多信息在Internet应用程序，请参见以下文章:  
  
-   [Internet第一步:ActiveX控件](../../mfc/activex-controls-on-the-internet.md)  
  
-   [Internet第一步:异步标记](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [MFC示例图像](../../top/visual-cpp-samples.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)