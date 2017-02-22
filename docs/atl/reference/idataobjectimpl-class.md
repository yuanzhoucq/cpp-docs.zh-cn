---
title: "IDataObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDataObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "data transfer [C++]"
  - "data transfer [C++], Uniform Data Transfer"
  - "IDataObject, ATL 实现"
  - "IDataObjectImpl class"
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IDataObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类支持合并数据传输和管理连接的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IDataObjectImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IDataObjectImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IDataObjectImpl::DAdvise](../Topic/IDataObjectImpl::DAdvise.md)|生成数据对象和建议接收器之间的连接。  这使建议接收器接收更改的通知在对象上的。|  
|[IDataObjectImpl::DUnadvise](../Topic/IDataObjectImpl::DUnadvise.md)|停止通过 `DAdvise`以前生成的连接。|  
|[IDataObjectImpl::EnumDAdvise](../Topic/IDataObjectImpl::EnumDAdvise.md)|创建枚举器循环访问当前通知连接。|  
|[IDataObjectImpl::EnumFormatEtc](../Topic/IDataObjectImpl::EnumFormatEtc.md)|创建枚举数将数据对象支持的 **FORMATETC** framework重复。  ATL实现返回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::FireDataChange](../Topic/IDataObjectImpl::FireDataChange.md)|将更改通知给每个建议接收器。|  
|[IDataObjectImpl::GetCanonicalFormatEtc](../Topic/IDataObjectImpl::GetCanonicalFormatEtc.md)|检索一个逻辑上等效的 **FORMATETC** framework为更复杂的一个。  ATL实现返回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::GetData](../Topic/IDataObjectImpl::GetData.md)|从数据对象将数据传输到客户端。  数据。**FORMATETC** 结构中描述和通过 **STGMEDIUM** 结构中传输。|  
|[IDataObjectImpl::GetDataHere](../Topic/IDataObjectImpl::GetDataHere.md)|类似于 `GetData`，除此之外，客户端必须分配 **STGMEDIUM** 结构。  ATL实现返回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::QueryGetData](../Topic/IDataObjectImpl::QueryGetData.md)|确定数据对象是否支持传输数据的特定 **FORMATETC** 结构。  ATL实现返回 **E\_NOTIMPL**。|  
|[IDataObjectImpl::SetData](../Topic/IDataObjectImpl::SetData.md)|从客户端将数据传输到数据对象。  ATL实现返回 **E\_NOTIMPL**。|  
  
## 备注  
 [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) 接口提供方法支持合并数据传输。  `IDataObject` 使用标准格式结构 [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) 和 [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) 检索和存储数据。  
  
 `IDataObject` 还会尝试连接建议接收器来处理数据更改通知。  为了客户端可以接收从数据对象中更改通知，客户端必须实现在调用建议接收器的对象的 [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) 接口。  当客户端然后调用 **IDataObject::DAdvise**时，建立连接后在数据对象和建议接收器之间。  
  
 选件类 `IDataObjectImpl` 提供 `IDataObject` 的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)