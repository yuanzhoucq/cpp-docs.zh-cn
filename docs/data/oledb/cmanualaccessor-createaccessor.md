---
title: "Cmanualaccessor:: Createaccessor |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs: C++
helpviewer_keywords: CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f313e6d2b13a03a91295c75d52e4e77d5dfda22b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
为列绑定结构分配内存和初始化列数据成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT CreateAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `nBindEntries`  
 [in]列数。 此数字应匹配对的调用数[cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)函数。  
  
 `pBuffer`  
 [in]指向输出列的存储位置的缓冲区的指针。  
  
 `nBufferSize`  
 [in]以字节为单位的缓冲区大小。  
  
## <a name="return-value"></a>返回值  
 一个标准`HRESULT`值。  
  
## <a name="remarks"></a>备注  
 调用此函数，然后才能调用`CManualAccessor::AddBindEntry`函数。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 示例](../../visual-cpp-samples.md)