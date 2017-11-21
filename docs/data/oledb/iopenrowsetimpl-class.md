---
title: "IOpenRowsetImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IOpenRowsetImpl
dev_langs: C++
helpviewer_keywords: IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89a37274fd4040b24c36983fea968674acf4fcab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl 类
提供有关实现`IOpenRowset`接口。  
  
## <a name="syntax"></a>语法  
  
```  
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### <a name="parameters"></a>参数  
 `SessionClass`  
 你的类，派生自`IOpenRowsetImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|创建一个行集对象。 不直接由用户调用。|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|打开并返回一个包括来自一个基表或索引的所有行的行集。 （不是在 ATLDB。H)|  
  
## <a name="remarks"></a>备注  
 [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)接口是必需的会话对象。 打开，并返回一个包括来自一个基表或索引的所有行的行集。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)