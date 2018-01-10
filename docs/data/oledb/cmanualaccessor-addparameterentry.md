---
title: "Cmanualaccessor:: Addparameterentry |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
dev_langs: C++
helpviewer_keywords: AddParameterEntry method
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 66c88bf072cbae6c86949d52ded121dd694c0e97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmanualaccessoraddparameterentry"></a>CManualAccessor::AddParameterEntry
将参数项添加到参数项结构。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void AddParameterEntry(  
   DBORDINAL nOrdinal,  
   DBTYPE wType,  
   DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT   
) throw ( );  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程序员参考*。  
  
 `nOrdinal`  
 [in]参数号。  
  
 `wType`  
 [in]数据类型。  
  
 `nColumnSize`  
 [in]以字节为单位的列大小。  
  
 `pData`  
 [in]指向存储在缓冲区中的列数据的指针。  
  
 `pLength`  
 [in]指向字段长度，如果所需的指针。  
  
 `pStatus`  
 [in]指向要将绑定到列的状态，如果所需的变量的指针。  
  
 *eParamIO*  
 [in]指定绑定与之关联的参数是否是一个输入、 输入/输出，或输出参数。  
  
## <a name="remarks"></a>备注  
 若要使用此功能，必须先调用[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [Cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [DBViewer 示例](../../visual-cpp-samples.md)