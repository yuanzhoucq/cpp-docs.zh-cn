---
title: CNoRowset 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e92c9bfb49bbb64faca633f04bb87f40028b6e1e
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339557"
---
# <a name="cnorowset-class"></a>CNoRowset 类
可以用作模板自变量 (`TRowset`) 用于[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md)。  
  
## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
### <a name="parameters"></a>参数  
 *TAccessor*  
 一个访问器类。 默认值为 `CAccessorBase`。  
  
## <a name="remarks"></a>备注  
 如果命令不返回行集，请将 `CNoRowset` 用作模板参数。  
  
 `CNoRowset` 将实现以下存根方法，其中每个方法都对应于其他访问器类方法：  
  
-   `BindFinished` -指示绑定操作何时完成 (返回`S_OK`)。  
  
-   `Close` -释放行和当前 IRowset 接口。  
  
-   `GetIID` - 检索连接点的接口 ID。  
  
-   `GetInterface` -检索接口。  
  
-   `GetInterfacePtr` - 检索封装的接口指针。  
  
-   `SetAccessor` -将指针设置为访问器。  
  
-   `SetupOptionalRowsetInterfaces` -设置设置为行集的可选接口。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)