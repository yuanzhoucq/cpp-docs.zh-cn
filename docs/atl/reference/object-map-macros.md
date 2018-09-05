---
title: 对象映射宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1061b105b7fd1e344223da3850275910c164774b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761847"
---
# <a name="object-map-macros"></a>对象映射宏

这些宏定义对象映射和条目。

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|可以指定将输入对象映射到的类对象的文本说明。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|在对象映射中输入的 ATL 对象、 更新注册表中，并创建对象的实例。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。|  

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION

可以指定您的类对象的文本说明。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>参数

*x*  
[in]类对象的说明。

### <a name="remarks"></a>备注

通过在对象映射到 ATL 进入此说明[OBJECT_ENTRY_AUTO](#object_entry_auto)宏。

实现 DECLARE_OBJECT_DESCRIPTION`GetObjectDescription`函数，可用于重写[CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription)方法。  

`GetObjectDescription`调用函数`IComponentRegistrar::GetComponents`。 `IComponentRegistrar` 是，可注册和注销 DLL 中的各个组件的自动化接口。 当使用 ATL 项目向导创建的支持组件注册对象时，该向导将自动执行`IComponentRegistrar`接口。 `IComponentRegistrar` 通常使用 Microsoft Transaction Server。

ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO

在对象映射中输入的 ATL 对象、 更新注册表中，并创建对象的实例。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>参数

*clsid*  
[in]由名为的 c + + 类实现的 COM 类的 CLSID*类*。

*class*  
[in]实现表示的 COM 类的 c + + 类名称*clsid*。

### <a name="remarks"></a>备注

对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。

OBJECT_ENTRY_AUTO 输入创建者类和类工厂创建者类的函数指针`CreateInstance`自动生成 ATL 对象映射到此对象的函数。 当[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)是调用，更新系统注册表对象映射中每个对象。  

下表描述了如何从第二个参数提供给此宏类获取添加到对象图的信息。

|有关的信息|从获取|
|---------------------|-------------------|
|COM 注册|[注册表宏](../../atl/reference/registry-macros.md)|
|类工厂创建|[类工厂宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|创建实例|[聚合宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|组件类别注册|[分类宏](../../atl/reference/category-macros.md)|
|类级别初始化和清理|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>参数

*clsid*  
[in]由名为的 c + + 类实现的 COM 类的 CLSID*类*。

*class*  
[in]实现表示的 COM 类的 c + + 类名称*clsid*。

### <a name="remarks"></a>备注

对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 允许您指定的对象应注册并初始化 (请参阅[OBJECT_ENTRY_AUTO](#object_entry_auto)有关详细信息)，但它不应为可通过创建`CoCreateInstance`。

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
