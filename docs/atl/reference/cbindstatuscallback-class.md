---
title: "CBindStatusCallback Class | Microsoft Docs"
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
  - "CBindStatusCallback"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous data transfer [C++]"
  - "CBindStatusCallback class"
  - "data transfer [C++]"
  - "data transfer [C++], 异步"
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBindStatusCallback Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此类实现 `IBindStatusCallback` 接口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <class   
      T  
      , int   
      nBindFlags  
      = BINDF_ASYNCHRONOUS |   
BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx  
<T::_ThreadModel::ThreadModelNoCS>, public IBindStatusCallbackImpl<T>   
```  
  
#### 参数  
 `T`  
 您的包含要调用作为数据功能的选件类接收。  
  
 *nBindFlags*  
 指定由 [GetBindInfo](../Topic/CBindStatusCallback::GetBindInfo.md)返回的绑定标志。  默认实现一组绑定是异步的，检索数据\/对象的新版本而不是缓存磁盘缓存存储检索的数据。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CBindStatusCallback::CBindStatusCallback](../Topic/CBindStatusCallback::CBindStatusCallback.md)|构造函数。|  
|[CBindStatusCallback::~CBindStatusCallback](../Topic/CBindStatusCallback::~CBindStatusCallback.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CBindStatusCallback::Download](../Topic/CBindStatusCallback::Download.md)|开始下载过程的静态方法，创建一 `CBindStatusCallback` 对象，并调用 `StartAsyncDownload`。|  
|[CBindStatusCallback::GetBindInfo](../Topic/CBindStatusCallback::GetBindInfo.md)|调用异步标记请求有关绑定的类型的信息创建。|  
|[CBindStatusCallback::GetPriority](../Topic/CBindStatusCallback::GetPriority.md)|调用异步标记获取绑定操作的优先级。  ATL实现返回 `E_NOTIMPL`。|  
|[CBindStatusCallback::OnDataAvailable](../Topic/CBindStatusCallback::OnDataAvailable.md)|调用提供数据。您的应用程序，它将变得可用。  读取数据，然后调用函数传递给它使用数据。|  
|[CBindStatusCallback::OnLowResource](../Topic/CBindStatusCallback::OnLowResource.md)|调用时，资源不足。  ATL实现返回 `S_OK`。|  
|[CBindStatusCallback::OnObjectAvailable](../Topic/CBindStatusCallback::OnObjectAvailable.md)|调用异步标记传递对象接口指针到您的应用程序。  ATL实现返回 `S_OK`。|  
|[CBindStatusCallback::OnProgress](../Topic/CBindStatusCallback::OnProgress.md)|调用指示数据下载的进度进程。  ATL实现返回 `S_OK`。|  
|[CBindStatusCallback::OnStartBinding](../Topic/CBindStatusCallback::OnStartBinding.md)|调用时，将启动。|  
|[CBindStatusCallback::OnStopBinding](../Topic/CBindStatusCallback::OnStopBinding.md)|调用，在异步数据传输停止。|  
|[CBindStatusCallback::StartAsyncDownload](../Topic/CBindStatusCallback::StartAsyncDownload.md)|初始化可用的字节，并读取字节为零，创建从URL的驱动器类型的流对象，并调用 `OnDataAvailable`，在数据可用时间。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[CBindStatusCallback::m\_dwAvailableToRead](../Topic/CBindStatusCallback::m_dwAvailableToRead.md)|可读取的字节数。|  
|[CBindStatusCallback::m\_dwTotalRead](../Topic/CBindStatusCallback::m_dwTotalRead.md)|读取的总字节数。|  
|[CBindStatusCallback::m\_pFunc](../Topic/CBindStatusCallback::m_pFunc.md)|调用函数的指针，当数据可用。|  
|[CBindStatusCallback::m\_pT](../Topic/CBindStatusCallback::m_pT.md)|对对象的请求的指针已发生异步数据传输。|  
|[CBindStatusCallback::m\_spBindCtx](../Topic/CBindStatusCallback::m_spBindCtx.md)|为 [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) 接口的指针当前绑定操作的。|  
|[CBindStatusCallback::m\_spBinding](../Topic/CBindStatusCallback::m_spBinding.md)|为 `IBinding` 接口的指针当前绑定操作的。|  
|[CBindStatusCallback::m\_spMoniker](../Topic/CBindStatusCallback::m_spMoniker.md)|为 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) 接口的指针URL中使用。|  
|[CBindStatusCallback::m\_spStream](../Topic/CBindStatusCallback::m_spStream.md)|为 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) 接口的指针数据传输的。|  
  
## 备注  
 `CBindStatusCallback` 类实现 `IBindStatusCallback` 接口。  必须由应用程序实现`IBindStatusCallback`，以便它可以接收异步数据传输的通知。  该系统提供的异步标记使用 `IBindStatusCallback` 方法向\/从对象中发送和获取有关异步数据传输的信息。  
  
 通常，`CBindStatusCallback` 与给定对象关联的绑定操作。  例如，在 [ASYNC](../../top/visual-cpp-samples.md) 示例，那么，当您设置URL属性时，它会创建在一个名为的 `CBindStatusCallback` 对象。`Download`:  
  
 [!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/CPP/cbindstatuscallback-class_1.h)]  
  
 在具有数据时，该异步标记使用回调函数 `OnData` 调用您的应用程序。  系统提供了异步标记。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 `IBindStatusCallback`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `CBindStatusCallback`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)