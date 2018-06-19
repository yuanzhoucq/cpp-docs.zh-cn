---
title: 'Ccommand:: Getparameterinfo |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- GetParameterInfo method
ms.assetid: 9cd9277f-0161-4bd8-ad24-58e5e90b92a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 869675c079a392bb1e1e96656e66ef7742f526c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094278"
---
# <a name="ccommandgetparameterinfo"></a>CCommand::GetParameterInfo
获取命令的参数、参数名称和参数类型的列表。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[ICommandWithParameters::GetParameterInfo](https://msdn.microsoft.com/en-us/library/ms714917.aspx)中*OLE DB 程序员参考*。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CCommand 类](../../data/oledb/ccommand-class.md)