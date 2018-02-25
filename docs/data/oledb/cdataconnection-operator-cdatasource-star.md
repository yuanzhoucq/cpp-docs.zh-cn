---
title: CDataConnection::operator CDataSource* | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
dev_langs:
- C++
helpviewer_keywords:
- CDataSource* operator
- operator * (CDataSource)
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60eba58d4a3884b191afdca1da0934453a303d8c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectionoperator-cdatasource"></a>CDataConnection::operator CDataSource*
返回指向包含的 `CDataSource` 对象的指针。  
  
## <a name="syntax"></a>语法  
  
```cpp
operator const CDataSource*() throw();  
  
```  
  
## <a name="remarks"></a>备注  
 此运算符将返回指向包含的 `CDataSource` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CDataSource` 指针）。  
  
 请参阅[运算符 CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)有关用法示例。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)