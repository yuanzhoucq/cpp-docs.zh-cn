---
title: "CNoRowset 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs: C++
helpviewer_keywords: CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 901d857b5095dd882a368b9a87e8a7d38d20bc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cnorowset-class"></a>CNoRowset 类
可用作模板自变量 (`TRowset`) 为[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### <a name="parameters"></a>参数  
 `TAccessor`  
 一个访问器类。 默认值为 `CAccessorBase`。  
  
## <a name="remarks"></a>备注  
 如果命令不返回行集，请将 `CNoRowset` 用作模板参数。  
  
 `CNoRowset` 将实现以下存根方法，其中每个方法都对应于其他访问器类方法：  
  
-   **BindFinished** -指示绑定完成 (返回`S_OK`)。  
  
-   **关闭**-释放行和当前 IRowset 接口。  
  
-   `GetIID` - 检索连接点的接口 ID。  
  
-   **GetInterface** -检索接口。  
  
-   `GetInterfacePtr` - 检索封装的接口指针。  
  
-   **SetAccessor** -对访问器中设置的指针。  
  
-   **SetupOptionalRowsetInterfaces** -设置为行集的可选接口。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)