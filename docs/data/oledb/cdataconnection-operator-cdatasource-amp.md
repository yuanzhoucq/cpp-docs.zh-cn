---
title: "Cdataconnection:: Operator CDataSource&amp; |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
dev_langs: C++
helpviewer_keywords:
- CDataSource& operator
- operator & (CDataSource)
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc2309b7b97a97d19ff9a68895fef3ed3bda8b7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>Cdataconnection:: Operator CDataSource&amp;
返回所包含的引用`CDataSource`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
operator const CDataSource&() throw( );  
  
```  
  
## <a name="remarks"></a>备注  
 此运算符返回对所包含的引用`CDataSource`对象，允许您传递`CDataConnection`对象其中`CDataSource`预期引用。  
  
## <a name="example"></a>示例  
 如果你具有某个函数 (如`func`下面) 采用`CDataSource`引用，你可以使用**CDataSource &**传递`CDataConnection`对象。  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)