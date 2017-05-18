---
title: "对象映射宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f03ca61c6ab3c550c316b380d34eb5fa4f3b61de
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="object-map-macros"></a>对象映射宏
这些宏定义对象映射和条目。  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|可以指定将对象映射到输入的类对象的文本说明。|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|ATL 对象进入对象映射、 更新注册表中，并创建对象的实例。|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
   
##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION  
 可以指定您的类对象的文本说明。  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]类对象的说明。  
  
### <a name="remarks"></a>备注  
 ATL 就会进入此说明在对象映射通过[OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd)宏。  
  
 `DECLARE_OBJECT_DESCRIPTION`实现`GetObjectDescription`函数，可用于重写[CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription)方法。  

  
 `GetObjectDescription`函数会由调用**IComponentRegistrar::GetComponents**。 **IComponentRegistrar**是一个自动化接口，允许您注册和注销的 DLL 中的各个组件。 当使用 ATL 项目向导创建组件注册器对象时，该向导将自动执行**IComponentRegistrar**接口。 **IComponentRegistrar**通常由 Microsoft Transaction Server。  
  
 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&123;](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO  
 ATL 对象进入对象映射、 更新注册表中，并创建对象的实例。  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 [in] 由名为 `class` 的 C++ 类实现的 COM 类的 CLSID。  
  
 `class`  
 [in] 实现由 `clsid` 表示的 COM 类的 C++ 类的名称。  
  
### <a name="remarks"></a>备注  
 对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。  
  
 `OBJECT_ENTRY_AUTO`输入的创建者类和类工厂创建者类的函数指针`CreateInstance`自动生成的 ATL 对象映射到此对象的函数。 当[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)是调用，它更新系统注册表，在对象映射中每个对象。  

  
 下表描述了如何从第二个参数提供给此宏的类获取的信息添加到对象映射。  
  
|有关的信息|从获取|  
|---------------------|-------------------|  
|COM 注册|[注册表宏](../../atl/reference/registry-macros.md)|  
|类工厂创建|[类工厂宏](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|创建实例|[聚合宏](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|组件类别注册|[类别宏](../../atl/reference/category-macros.md)|  
|类级别初始化和清理代码|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>参数  
 `clsid`  
 [in] 由名为 `class` 的 C++ 类实现的 COM 类的 CLSID。  
  
 `class`  
 [in] 实现由 `clsid` 表示的 COM 类的 C++ 类的名称。  
  
### <a name="remarks"></a>备注  
 对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`允许您指定的对象应注册并初始化 (请参阅[OBJECT_ENTRY_AUTO](#object_entry_auto)有关详细信息)，但不是应将可通过创建`CoCreateInstance`。  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

