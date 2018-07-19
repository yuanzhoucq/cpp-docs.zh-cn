---
title: 'Cdataconnection:: Copy |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method
ms.assetid: a3dbd70d-36be-49e0-a527-00e3910a7a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9264b29a0a5a5df3b80434e0977431fa16ba24a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096163"
---
# <a name="cdataconnectioncopy"></a>CDataConnection::Copy
创建现有的数据连接的副本。  
  
## <a name="syntax"></a>语法  
  
```cpp
      CDataConnection& Copy(const CDataConnection & ds) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `ds`  
 [in]对现有的数据连接将复制的引用。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)