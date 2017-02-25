---
title: "IPersistStorageImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IPersistStorageImpl"
  - "ATL::IPersistStorageImpl<T>"
  - "ATL.IPersistStorageImpl<T>"
  - "IPersistStorageImpl"
  - "ATL.IPersistStorageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistStorageImpl class"
  - "存储, ATL"
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPersistStorageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) 接口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T  
>  
class ATL_NO_VTABLE IPersistStorageImpl :  
public IPersistStorage  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IPersistStorageImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IPersistStorageImpl::GetClassID](../Topic/IPersistStorageImpl::GetClassID.md)|检索对象的CLSID。|  
|[IPersistStorageImpl::HandsOffStorage](../Topic/IPersistStorageImpl::HandsOffStorage.md)|指示对象释放所有存储对象和输入HandsOff模式。  ATL实现返回 `S_OK`。|  
|[IPersistStorageImpl::InitNew](../Topic/IPersistStorageImpl::InitNew.md)|初始化新的存储。|  
|[IPersistStorageImpl::IsDirty](../Topic/IPersistStorageImpl::IsDirty.md)|检查对象的数据是否已更改，则它上次保存了。|  
|[IPersistStorageImpl::Load](../Topic/IPersistStorageImpl::Load.md)|从指定的存储填充对象的属性。|  
|[IPersistStorageImpl::Save](../Topic/IPersistStorageImpl::Save.md)|保存对象的属性设置为指定的存储。|  
|[IPersistStorageImpl::SaveCompleted](../Topic/IPersistStorageImpl::SaveCompleted.md)|通知对象则可能返回到普通模式写入到其存储对象。  ATL实现返回 `S_OK`。|  
  
## 备注  
 `IPersistStorageImpl` 实现 [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) 接口，使用存储，以允许客户端请求您的对象加载和保存其持久性数据。  
  
 此选件类的实现要求选件类 `T` 进行实现 `IPersistStreamInit` 接口可通过 `QueryInterface`。  这通常意味着选件类 `T` 应从 [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)派生，请在 [COM映射](../Topic/BEGIN_COM_MAP.md)的 `IPersistStreamInit` 提供项和使用 [属性映射](../Topic/BEGIN_PROP_MAP.md) 描述选件类的持久性数据。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Storages and Streams](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [IPersistStreamInitImpl Class](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl Class](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)