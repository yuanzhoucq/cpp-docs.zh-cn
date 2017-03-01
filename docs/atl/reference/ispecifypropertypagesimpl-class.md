---
title: "ISpecifyPropertyPagesImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATL.ISpecifyPropertyPagesImpl<T>
- ATL::ISpecifyPropertyPagesImpl
- ATL::ISpecifyPropertyPagesImpl<T>
- ATL.ISpecifyPropertyPagesImpl
- ISpecifyPropertyPagesImpl Class
dev_langs:
- C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4d5f74de2ec6569527221cf94df6f7921f4bb4c9
ms.lasthandoff: 02/24/2017

---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl 类
此类实现**IUnknown** ，并提供的默认实现[ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217)接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`ISpecifyPropertyPagesImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|填充的 UUID 计数数组值。 每个 UUID 对应于一个可以在对象的属性表中显示的属性页的 CLSID。|  
  
## <a name="remarks"></a>备注  
 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217)接口允许客户端获取支持的对象的属性页的 Clsid 的列表。 类`ISpecifyPropertyPagesImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
> [!NOTE]
>  不要公开**ISpecifyPropertyPages**接口如果您的对象不支持属性页。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namegetpagesa--ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages  
 填充数组[CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048)结构可以在对象的属性表中显示的属性页的 Clsid。  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射检索每个 CLSID。  
  
 请参阅[ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)   
 [IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

