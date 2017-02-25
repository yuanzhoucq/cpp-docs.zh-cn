---
title: "CAsyncMonikerFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAsyncMonikerFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 异步"
  - "asynchronous controls [C++]"
  - "CAsyncMonikerFile class"
  - "IMoniker interface, 绑定"
  - "monikers [C++], MFC"
  - "OLE 控件 [C++], 异步"
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAsyncMonikerFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供了用于在ActiveX控件\(原来为OLE控件\)的异步标记的使用。  
  
## 语法  
  
```  
class CAsyncMonikerFile : public CMonikerFile  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAsyncMonikerFile::CAsyncMonikerFile](../Topic/CAsyncMonikerFile::CAsyncMonikerFile.md)|构造 `CAsyncMonikerFile` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAsyncMonikerFile::Close](../Topic/CAsyncMonikerFile::Close.md)|关闭并释放所有资源。|  
|[CAsyncMonikerFile::GetBinding](../Topic/CAsyncMonikerFile::GetBinding.md)|检索指向异步传输绑定。|  
|[CAsyncMonikerFile::GetFormatEtc](../Topic/CAsyncMonikerFile::GetFormatEtc.md)|检索数据的格式在流的。|  
|[CAsyncMonikerFile::Open](../Topic/CAsyncMonikerFile::Open.md)|打开文件异步。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](../Topic/CAsyncMonikerFile::CreateBindStatusCallback.md)|创建COM对象实现 `IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](../Topic/CAsyncMonikerFile::GetBindInfo.md)|调用由OLE系统库请求有关绑定的类型的信息创建。|  
|[CAsyncMonikerFile::GetPriority](../Topic/CAsyncMonikerFile::GetPriority.md)|调用由OLE系统库来获取绑定的优先级。|  
|[CAsyncMonikerFile::OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md)|调用提供数据，则它将成为可供客户端在异步绑定操作中|  
|[CAsyncMonikerFile::OnLowResource](../Topic/CAsyncMonikerFile::OnLowResource.md)|调用时，资源不足。|  
|[CAsyncMonikerFile::OnProgress](../Topic/CAsyncMonikerFile::OnProgress.md)|调用指示在数据下载的进度进程。|  
|[CAsyncMonikerFile::OnStartBinding](../Topic/CAsyncMonikerFile::OnStartBinding.md)|调用时，将启动。|  
|[CAsyncMonikerFile::OnStopBinding](../Topic/CAsyncMonikerFile::OnStopBinding.md)|调用，在异步传输停止。|  
  
## 备注  
 从 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)派生，从 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)而后者派生，`CAsyncMonikerFile` 使用 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) 接口访问所有数据流异步，包括加载文件从URL异步。  文件可以是ActiveX控件datapath属性。  
  
 异步标记主要在Internet上启用的应用程序和ActiveX控件使用提供具有响应能力的用户界面在文件传输过程。  这种情况的一个光辉的示例是使用 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) 为ActiveX控件提供异步属性。  `CDataPathProperty` 对象会反复指示的回调新数据的可用性在一个长属性交换过程中处理。  
  
 有关如何使用异步标记和ActiveX控件的更多信息在Internet应用程序，请参见以下文章:  
  
-   [Internet第一步:异步标记](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Internet第一步:ActiveX控件](../../mfc/activex-controls-on-the-internet.md)  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C文件](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [CMonikerFile Class](../../mfc/reference/cmonikerfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMonikerFile Class](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)   
 [Asynchronous Versus Synchronous Monikers](http://msdn.microsoft.com/library/windows/desktop/ms687193)