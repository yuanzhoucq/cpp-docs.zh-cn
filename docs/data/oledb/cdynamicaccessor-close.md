---
title: CDynamicAccessor::Close | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 2a28ded2-d7ed-4e80-90bf-143133c93feb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7fb83230b3dda03ee179872d34cf2515ac5d1f2a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorclose"></a>CDynamicAccessor::Close
取消绑定所有列，释放分配的内存，并释放[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)类中的接口指针。  
  
## <a name="syntax"></a>语法  
  
```cpp
void Close() throw();  
  
```  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)