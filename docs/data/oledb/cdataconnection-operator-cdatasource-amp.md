---
title: 'Cdataconnection:: Operator CDataSource&amp; |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8aca05cd83123e2866b8d46e5d5f085b5edd04f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093423"
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>Cdataconnection:: Operator CDataSource&amp;
返回所包含的引用`CDataSource`对象。  
  
## <a name="syntax"></a>语法  
  
```cpp
operator const CDataSource&() throw();  
  
```  
  
## <a name="remarks"></a>备注  
 此运算符返回对所包含的引用`CDataSource`对象，允许您传递`CDataConnection`对象其中`CDataSource`预期引用。  
  
## <a name="example"></a>示例  
 如果你具有某个函数 (如`func`下面) 采用`CDataSource`引用，你可以使用**CDataSource &** 传递`CDataConnection`对象。  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)