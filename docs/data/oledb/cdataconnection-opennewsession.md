---
title: "Cdataconnection:: Opennewsession |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
dev_langs:
- C++
helpviewer_keywords:
- OpenNewSession method
ms.assetid: 0a70e573-9498-4ca7-b524-45666dc7b0a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65b20285bc46fddb8002a95ff77ce21c7a1018e5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectionopennewsession"></a>CDataConnection::OpenNewSession
打开新会话使用当前连接对象的数据源。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT OpenNewSession(CSession & session) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `session`  
 [输入/输出]对新的会话对象的引用。  
  
 **备注**  
 在新的会话使用当前连接对象的包含的数据源对象作为其父级，并且可以访问所有数据源相同的信息。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)