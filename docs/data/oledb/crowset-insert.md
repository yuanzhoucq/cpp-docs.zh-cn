---
title: "Crowset:: Insert |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.Insert
- CRowset.Insert
- CRowset<TAccessor>.Insert
- CRowset<TAccessor>::Insert
- ATL::CRowset<TAccessor>::Insert
- ATL.CRowset.Insert
- CRowset::Insert
- ATL::CRowset::Insert
dev_langs:
- C++
helpviewer_keywords:
- Insert method
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d23396664788f6509b64f9aae88eb9674586fbf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetinsert"></a>CRowset::Insert
创建并初始化新行使用访问器中的数据。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT Insert(int nAccessor = 0,   
   bool bGetHRow = false) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `nAccessor`  
 [in]访问器可用于插入数据的数。  
  
 *bGetHRow*  
 [in]指示是否检索为插入的行的句柄。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法要求的可选接口`IRowsetChange`，这可能不支持对所有提供程序，如果出现这种情况，该方法返回**E_NOINTERFACE**。 你还必须设置**DBPROP_IRowsetChange**到`VARIANT_TRUE`之前调用**打开**对表或命令，其中包含行集。  
  
 如果一个或多个列是不可写，则插入可能会失败。 修改光标映射以更正此问题。  
  
## <a name="example"></a>示例  
 下面的示例演示如何通过行集访问数据源，然后插入使用表格，在该行集的字符串。  
  
 首先，通过将新的 ATL 对象插入到你的项目中创建表类。 例如，右键单击工作区窗格中的项目并选择**新 ATL 对象**。 从**数据访问**类别中，选择**使用者**。 创建类型的使用者对象**表**。 (选择**表**直接从表中创建行集; 选择**命令**创建通过 SQL 命令的行集。)选择数据源，指定要用来访问该数据源的表。 如果调用使用者对象**CCustomerTable**，然后将实现你插入的代码，如下所示：  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/cpp/crowset-insert_1.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CRowset 类](../../data/oledb/crowset-class.md)