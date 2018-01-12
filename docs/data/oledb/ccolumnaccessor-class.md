---
title: "CColumnAccessor 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs: C++
helpviewer_keywords: CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 55c77a53cb6e6c4a103c509aa3d527803d91af3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor 类
生成注入的使用者代码。  
  
## <a name="syntax"></a>语法  
  
```  
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>备注  
 在注入的代码中，每个列作为单独的访问器绑定。 您应该知道，此类在注入的代码中使用（例如，您可能在调试遇到此警告），但您通常不必直接使用此类或其方法。  
  
 `CColumnAccessor` 可实现以下存根方法，每个方法在功能上对应于其他访问器类方法：  
  
-   `CColumnAccessor`构造函数;实例化和初始化`CColumnAccessor`对象。  
  
-   `CreateAccessor`为列绑定结构分配内存和初始化列数据成员。  
  
-   **BindColumns**将列绑定到访问器。  
  
-   **SetParameterBuffer**为参数分配缓冲区。  
  
-   `AddParameter`将参数项添加到参数项结构。  
  
-   **HasOutputColumns**确定访问器是否有输出列  
  
-   **HasParameters**确定访问器是否有参数。  
  
-   `BindParameters`将创建的参数绑定到列。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)