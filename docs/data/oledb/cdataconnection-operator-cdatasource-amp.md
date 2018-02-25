---
title: CDataConnection::operator CDataSource&amp; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
dev_langs:
- C++
helpviewer_keywords:
- CDataSource& operator
- operator & (CDataSource)
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 255d1fe1d6363277c300fee134c5c41473ee8c3b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>CDataConnection::operator CDataSource&amp;
返回所包含的引用`CDataSource`对象。  
  
## <a name="syntax"></a>语法  
  
```cpp
operator const CDataSource&() throw();  
  
```  
  
## <a name="remarks"></a>备注  
 此运算符返回对所包含的引用`CDataSource`对象，允许您传递`CDataConnection`对象其中`CDataSource`预期引用。  
  
## <a name="example"></a>示例  
 如果你具有某个函数 (如`func`下面) 采用`CDataSource`引用，你可以使用**CDataSource &**传递`CDataConnection`对象。  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)