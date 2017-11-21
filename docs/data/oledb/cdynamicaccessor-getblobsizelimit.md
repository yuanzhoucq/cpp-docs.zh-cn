---
title: "Cdynamicaccessor:: Getblobsizelimit |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
dev_langs: C++
helpviewer_keywords: GetBlobSizeLimit method
ms.assetid: 7131e7c4-6e05-42f3-9d87-110301b672f2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e1ebfa3085e5c0a1f7b8392e5be8f7bca5de9af9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetblobsizelimit"></a>CDynamicAccessor::GetBlobSizeLimit
检索以字节为单位的最大 BLOB 大小。  
  
## <a name="syntax"></a>语法  
  
```  
  
const DBLENGTH GetBlobSizeLimit( ) const;  
  
```  
  
## <a name="remarks"></a>备注  
 返回 BLOB 处理值`nBlobSize`由中设置[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)