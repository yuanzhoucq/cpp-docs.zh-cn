---
title: "CAtlAutoThreadModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlAutoThreadModule
- CAtlAutoThreadModule
- ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 09f4a7061ce1e4a09d0d27bd90dfcc16a37f4d5b
ms.lasthandoff: 02/24/2017

---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule 类
此类实现线程池、 单元模型的 COM 服务器。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>备注  
 `CAtlAutoThreadModule`派生自[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)并实现线程池、 单元模型的 COM 服务器。 `CAtlAutoThreadModule`使用[CComApartment](../../atl/reference/ccomapartment-class.md)来管理模块中的每个线程单元。  
  
 必须使用[DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f)中对象的类定义，以指定宏[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)作为类工厂。 然后，您应该添加派生自的类的单个实例`CAtlAutoThreadModuleT`如`CAtlAutoThreadModule`。 例如:   
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  此类替换已过时[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlbase.h  
  
## <a name="see-also"></a>另请参阅  
 [CAtlAutoThreadModuleT 类](../../atl/reference/catlautothreadmodulet-class.md)   
 [IAtlAutoThreadModule 类](../../atl/reference/iatlautothreadmodule-class.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)
