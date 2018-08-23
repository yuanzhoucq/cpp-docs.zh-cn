---
title: IConvertTypeImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e176cc20dc3f6f13eb868133b99c0ce7e86d25c4
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573028"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl 类
提供的实现[IConvertType](/previous-versions/windows/desktop/ms715926\(v=vs.85\))接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IConvertTypeImpl`。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[CanConvert](#canconvert)|命令或上一个行集提供类型转换的可用性的信息。|  
  
## <a name="remarks"></a>备注  
 此接口是必需的对于命令、 行集和索引行集。 `IConvertTypeImpl` 通过将委派给提供的 OLE DB 转换对象实现的接口。  

## <a name="canconvert"></a> Iconverttypeimpl:: Canconvert
命令或上一个行集提供类型转换的可用性的信息。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IConvertType::CanConvert](/previous-versions/windows/desktop/ms711224\(v=vs.85\))中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  
 使用 OLE DB 中的数据转换`MSADC.DLL`。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)