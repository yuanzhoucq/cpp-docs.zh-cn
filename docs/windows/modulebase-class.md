---
title: "ModuleBase 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ModuleBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ModuleBase 类"
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ModuleBase 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>备注  
 表示类的基类 [模块](../windows/module-class.md) 类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Modulebase:: Modulebase 构造函数](../windows/modulebase-modulebase-constructor.md)|初始化 Module 类的实例。|  
|[ModuleBase:: ~ ModuleBase 析构函数](../windows/modulebase-tilde-modulebase-destructor.md)|取消初始化 Module 类的当前实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Modulebase:: Decrementobjectcount 方法](../windows/modulebase-decrementobjectcount-method.md)|在实现时，递减的对象数跟踪模块。|  
|[Modulebase:: Incrementobjectcount 方法](../windows/modulebase-incrementobjectcount-method.md)|在实现时，会递增模块所跟踪的对象的数目。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ModuleBase`  
  
## <a name="requirements"></a>要求  
 **标头︰** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)