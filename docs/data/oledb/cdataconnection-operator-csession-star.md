---
title: "Cdataconnection:: Operator CSession * |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs: C++
helpviewer_keywords:
- operator CSession*
- CSession* operator
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c4ad47ce5163291c45827d94c9e6f8d5904c847
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-csession"></a>CDataConnection::operator CSession*
返回指向包含的 `CSession` 对象的指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
operator const CSession*() throw( );  
  
```  
  
## <a name="remarks"></a>备注  
 此运算符将返回指向包含的 `CSession` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CSession` 指针）。  
  
## <a name="example"></a>示例  
 请参阅[运算符 CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)有关用法示例。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)