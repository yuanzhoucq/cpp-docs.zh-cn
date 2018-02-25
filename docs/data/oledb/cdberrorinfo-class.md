---
title: "CDBErrorInfo 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ae65a1a04d5befdfcd22327def8f60d96c9d4cff
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 类
提供对 OLE DB 错误处理使用 OLE DB 支持[IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
class CDBErrorInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|返回错误记录中包含的所有错误信息。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|调用[IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx)返回有关指定的错误的基本信息。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|调用[IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx)以对自定义错误对象返回到接口的指针。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|调用[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)返回**IErrorInfo**到指定的记录的接口指针。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|调用[IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx)返回错误参数。|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|获取指定对象的错误记录。|  
  
## <a name="remarks"></a>备注  
 此接口向用户返回一个或多个错误记录。 调用[cdberrorinfo:: Geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)首先，需要获得的错误记录计数。 然后调用一个访问函数，如[cdberrorinfo:: Getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)来检索每个记录的错误信息。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)