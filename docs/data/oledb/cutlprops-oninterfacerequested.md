---
title: "Cutlprops:: Oninterfacerequested |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps
dev_langs:
- C++
helpviewer_keywords:
- OnInterfaceRequested method
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eb15d2574ba60dcec9c0638ca10a465db5813709
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsoninterfacerequested"></a>CUtlProps::OnInterfaceRequested
处理请求的可选接口，使用者调用方法时对象之一上创建接口。  
  
## <a name="syntax"></a>语法  
  
```cpp
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 [in]所请求的接口的 IID。 有关更多详细信息，请参阅说明`riid`参数`ICommand::Execute`中*OLE DB 程序员参考*(在*MDAC SDK*)。  
  
## <a name="remarks"></a>备注  
 **OnInterfaceRequested**处理可选接口的使用者请求时使用者调用的方法的对象之一上创建接口 (如**IDBCreateSession**， **IDBCreateCommand**， `IOpenRowset`，或`ICommand`)。 它设置为所请求的接口对应的 OLE DB 属性。 例如，如果使用者请求**IID_IRowsetLocate**， **OnInterfaceRequested**设置**DBPROP_IRowsetLocate**接口。 这样在行集创建过程中维护的正确状态。  
  
 当使用者调用时调用此方法**IOpenRowset::OpenRowset**或`ICommand::Execute`。  
  
 如果使用者将打开一个对象，且请求的可选接口，与该接口关联的属性应设置提供程序`VARIANT_TRUE`。 若要允许特定于属性处理**OnInterfaceRequested**之前提供程序的调用**执行**调用方法。 默认情况下， **OnInterfaceRequested**处理以下接口：  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 如果你想要处理其他界面，重写此函数在您的数据源、 会话、 命令或行集类到进程函数中。 重写应经历正常的集获取属性接口，以确保，设置属性也将设置任何链接的属性 (请参阅[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md))。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [CUtlProps 类](../../data/oledb/cutlprops-class.md)