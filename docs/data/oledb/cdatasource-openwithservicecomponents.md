---
title: "Cdatasource:: Openwithservicecomponents |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
dev_langs: C++
helpviewer_keywords: OpenWithServiceComponents method
ms.assetid: 49c1d037-36ae-4fde-8e54-ced623abe1a9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87ccbbd178de3e8a724e65a04a04319a90b7a311
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourceopenwithservicecomponents"></a>CDataSource::OpenWithServiceComponents
使用 oledb32.dll 中的服务组件打开数据源对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT OpenWithServiceComponents (  
   const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
HRESULT OpenWithServiceComponents (  
   LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1   
);  
```  
  
#### <a name="parameters"></a>参数  
 `clsid`  
 [in]**CLSID**数据提供程序。  
  
 `szProgID`  
 [in] 数据提供程序的程序 ID。  
  
 `pPropset`  
 [in]指向数组的指针[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)包含属性和要设置值的结构。 请参阅[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程序员参考*Windows SDK 中。 如果数据源对象进行初始化，则属性必须属于数据源属性组。 如果同一个属性在 `pPropset` 中多次指定，则使用的值特定于提供程序。 如果 `ulPropSets` 为零，则忽略此参数。  
  
 `ulPropSets`  
 [in]数[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构*pPropSet*自变量。 如果这是零，则提供程序会忽略 `pPropset`。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅"OLE DB 服务"上的 OLE DB 程序员参考中[http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)