---
title: "IPersistStreamInitImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: aa8427a891ac8d8e18ec7794a12e838a55bc23c8
ms.lasthandoff: 02/24/2017

---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl 类
此类实现**IUnknown** ，并提供的默认实现[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPersistStreamInitImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|检索对象的 CLSID。|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|检索保存对象的数据所需的流的大小。 ATL 实现返回**E_NOTIMPL**。|  
|[IPersistStreamInitImpl::InitNew](#initnew)|初始化新创建的对象。|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|检查自上次保存后，该对象的数据是否已更改。|  
|[IPersistStreamInitImpl::Load](#load)|从指定的流加载对象的属性。|  
|[IPersistStreamInitImpl::Save](#save)|将对象的属性保存到指定的流。|  
  
## <a name="remarks"></a>备注  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)接口允许客户端请求您的对象加载，并将其永久数据保存到单个流。 类`IPersistStreamInitImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStreamInitImpl::GetClassID  
 检索对象的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax  
 检索保存对象的数据所需的流的大小。  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="initnew"></a>IPersistStreamInitImpl::InitNew  
 初始化新创建的对象。  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isdirty"></a>IPersistStreamInitImpl::IsDirty  
 检查自上次保存后，该对象的数据是否已更改。  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="load"></a>IPersistStreamInitImpl::Load  
 从指定的流加载对象的属性。  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来检索此信息。  
  
 请参阅[IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="save"></a>IPersistStreamInitImpl::Save  
 将对象的属性保存到指定的流。  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来存储此信息。  
  
 请参阅[IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [存储和流](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [类概述](../../atl/atl-class-overview.md)

