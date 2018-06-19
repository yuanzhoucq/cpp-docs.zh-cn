---
title: 'Iaccessorimpl:: Createaccessor |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
dev_langs:
- C++
helpviewer_keywords:
- CreateAccessor method
ms.assetid: f6b92075-c0b8-46ca-8361-026d562d24f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9a45c76deb0dfd196f90412845d56c753cfd0903
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099545"
---
# <a name="iaccessorimplcreateaccessor"></a>IAccessorImpl::CreateAccessor
从一组绑定创建一个访问器。  
  
## <a name="syntax"></a>语法  
  
```cpp
      STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[IAccessor::CreateAccessor](https://msdn.microsoft.com/en-us/library/ms720969.aspx)中*OLE DB 程序员参考*。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [IAccessorImpl 类](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)