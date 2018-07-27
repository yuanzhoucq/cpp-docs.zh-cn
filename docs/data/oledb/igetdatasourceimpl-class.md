---
title: IGetDataSourceImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 558578a82f1906d7481abebc5e1f1719b1983724
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269932"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl 类
提供的实现[IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx)对象。  
  
## <a name="syntax"></a>语法

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IGetDataSourceImpl`。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetDataSource](#getdatasource)|在创建会话的数据源对象上返回的接口指针。|  
  
## <a name="remarks"></a>备注  
 用于获取数据源对象的接口指针的会话，这是必需的接口。  

## <a name="getdatasource"></a> Igetdatasourceimpl:: Getdatasource
在创建会话的数据源对象上返回的接口指针。  
  
### <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IGetDataSource::GetDataSource](https://msdn.microsoft.com/library/ms725443.aspx)中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  
 如果你需要访问数据源对象中的属性，这很有用。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
