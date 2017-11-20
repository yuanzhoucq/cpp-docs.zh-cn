---
title: "Cdataconnection:: Cdataconnection |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs: C++
helpviewer_keywords: CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e92019f3f49257e297bddb2f717cf416da62a3bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
实例化和初始化`CDataConnection`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      CDataConnection();   
CDataConnection(  
   const CDataConnection &ds  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ds`  
 [in]对现有的数据连接的引用。  
  
## <a name="remarks"></a>备注  
 第一个重写创建一个新`CDataConnection`使用默认设置的对象。  
  
 第二个重写创建一个新`CDataConnection`使用等效于指定类型的数据连接对象的设置的对象。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [CDataConnection 类](../../data/oledb/cdataconnection-class.md)