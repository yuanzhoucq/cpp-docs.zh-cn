---
title: "CManualAccessor 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs: C++
helpviewer_keywords: CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f32046f36aefa2c19c8c364f7598a06b71d71bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 类
表示用于高级用途设计一个访问器类型。  
  
## <a name="syntax"></a>语法  
  
```  
class CManualAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|将绑定条目添加到输出列。|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|将参数项添加到参数访问器。|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|为列绑定结构分配内存和初始化列数据成员。|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|参数绑定结构分配内存和初始化参数数据成员。|  
  
## <a name="remarks"></a>备注  
 使用`CManualAccessor`，你可以指定参数和输出列绑定的运行时函数调用。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)