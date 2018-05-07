---
title: IErrorRecordsImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0d0425e7765cf09abb870cb39720cf43c8c74174
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 类
实现 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx)接口，添加到的记录并从数据成员中检索的记录 ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) 类型的**CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 从派生的类`IErrorRecordsImpl`。  
  
 `RecordClass`  
 一个类，表示 OLE DB 对象时出错。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|获取从错误记录的错误描述字符串。|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|获取从错误记录错误 GUID。|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|从错误记录中获取的帮助上下文 ID。|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|从错误记录中获取的帮助文件的完整路径名。|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|获取从错误记录错误的源代码。|  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|将记录添加到 OLE DB 错误对象。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|返回有关错误，如返回代码和提供程序特定的错误数的基本信息。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|返回一个指向接口上的自定义错误对象。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|返回[IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx)上指定的记录的接口指针。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|返回的错误参数。|  
|[GetRecordCount](../../mfc/reference/cdaorecordset-class.md#getrecordcount)|在 OLE DB 记录对象中返回记录的数。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|错误记录的数组。|  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)