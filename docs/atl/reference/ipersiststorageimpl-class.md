---
title: "IPersistStorageImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a5a855f81072316510efb47c3f9650a5feafa39b
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl 类
此类实现[IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731)接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPersistStorageImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|检索对象的 CLSID。|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|指示要释放所有存储对象，并进入 HandsOff 模式的对象。 ATL 实现返回`S_OK`。|  
|[IPersistStorageImpl::InitNew](#initnew)|初始化新的存储。|  
|[IPersistStorageImpl::IsDirty](#isdirty)|检查自上次保存后，该对象的数据是否已更改。|  
|[IPersistStorageImpl::Load](#load)|从指定的存储中加载该对象的属性。|  
|[IPersistStorageImpl::Save](#save)|将对象的属性保存到指定的存储。|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|通知它可以返回到正常模式要写入到它的存储对象的对象。 ATL 实现返回`S_OK`。|  
  
## <a name="remarks"></a>备注  
 `IPersistStorageImpl`实现[IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731)接口，这允许客户端请求的对象加载和保存使用存储其持久性数据。  
  
 此类的实现需要类`T`使的实现`IPersistStreamInit`接口可通过`QueryInterface`。 通常这意味着该类`T`应派生自[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)，提供的条目`IPersistStreamInit`中[COM 映射](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)，并使用[属性映射](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427)来描述类的持久性数据。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStorageImpl::GetClassID  
 检索对象的 CLSID。  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage  
 指示要释放所有存储对象，并进入 HandsOff 模式的对象。  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="initnew"></a>IPersistStorageImpl::InitNew  
 初始化新的存储。  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>备注  
 ATL 实现委托给[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)接口。  
  
 请参阅[IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isdirty"></a>IPersistStorageImpl::IsDirty  
 检查自上次保存后，该对象的数据是否已更改。  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>备注  
 ATL 实现委托给[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)接口。  
  
 请参阅[IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="load"></a>IPersistStorageImpl::Load  
 从指定的存储中加载该对象的属性。  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>备注  
 ATL 实现委托给[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)接口。 **负载**使用名为"目录"的流中检索对象的数据。 [保存](#save)方法最初创建此流。  
  
 请参阅[IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="save"></a>IPersistStorageImpl::Save  
 将对象的属性保存到指定的存储。  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>备注  
 ATL 实现委托给[IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273)接口。 当**保存**第一次调用时，创建指定的存储上名为"目录"的流。 此流随后将用于对更高版本调用**保存**和对的调用[负载](#load)。  
  
 请参阅[IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted  
 通知它可以返回到正常模式要写入到它的存储对象的对象。  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
### <a name="remarks"></a>备注  
 请参阅[IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [存储和流](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [IPersistStreamInitImpl 类](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl 类](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

