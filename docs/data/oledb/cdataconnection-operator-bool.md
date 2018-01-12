---
title: "Cdataconnection:: Operator BOOL |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs: C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: ad0bea7f-61ff-47f7-8127-32a31e3e9b9d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 342a8074f61a6f05505534ff497010b8a752293c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdataconnectionoperator-bool"></a>CDataConnection::operator BOOL
确定当前会话是否为打开。  
  
## <a name="syntax"></a>语法  
  
```  
  
operator BOOL( ) throw( );  
  
```  
  
## <a name="remarks"></a>备注  
 返回**BOOL** (MFC typedef) 值。 **TRUE**意味着当前会话处于打开状态;**FALSE**意味着关闭当前会话。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [Cdataconnection:: Operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)