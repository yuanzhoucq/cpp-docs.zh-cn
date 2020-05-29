---
title: 对象映射宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326217"
---
# <a name="object-map-macros"></a>对象映射宏

这些宏定义对象映射和条目。

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|允许您指定类对象的文本描述，该描述将输入到对象映射中。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|将 ATL 对象输入对象映射，更新注册表，并创建对象的实例。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

允许您为类对象指定文本说明。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]类对象的描述。

### <a name="remarks"></a>备注

ATL 通过[OBJECT_ENTRY_AUTO](#object_entry_auto)宏将此描述输入到对象映射中。

DECLARE_OBJECT_DESCRIPTION实现一`GetObjectDescription`个函数，可用于重写[CComCoClass：：getObject 描述](ccomcoclass-class.md#getobjectdescription)方法。

函数`GetObjectDescription`由 调用`IComponentRegistrar::GetComponents`。 `IComponentRegistrar`是一个自动化接口，允许您在 DLL 中注册和取消注册单个组件。 使用 ATL 项目向导创建组件注册器对象时，向导将自动实现`IComponentRegistrar`接口。 `IComponentRegistrar`通常用于 Microsoft 事务服务器。

有关 ATL 项目向导的详细信息，请参阅创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)的文章。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

将 ATL 对象输入对象映射，更新注册表，并创建对象的实例。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>参数

*Clsid*<br/>
[在]由名为*类*的C++类实现的 COM 类的 CLSID。

*class*<br/>
[在]实现由*clsid*表示的 COM 类的C++类的名称。

### <a name="remarks"></a>备注

对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。

OBJECT_ENTRY_AUTO此对象的创建者类和类工厂创建者类`CreateInstance`函数的函数指针输入到自动生成的 ATL 对象映射中。 当调用[CAtlComModule：注册服务器](catlcommodule-class.md#registerserver)时，它会更新对象映射中每个对象的系统注册表。

下表描述了如何从作为此宏的第二个参数给出的类获取添加到对象映射的信息。

|信息|从|
|---------------------|-------------------|
|COM 注册|[注册表宏](../../atl/reference/registry-macros.md)|
|类工厂创建|[类工厂宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|实例创建|[聚合宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|组件类别注册|[分类宏](../../atl/reference/category-macros.md)|
|类级初始化和清理|[对象主](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>参数

*Clsid*<br/>
[在]由名为*类*的C++类实现的 COM 类的 CLSID。

*class*<br/>
[在]实现由*clsid*表示的 COM 类的C++类的名称。

### <a name="remarks"></a>备注

对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO允许您指定应注册和初始化对象（有关详细信息[，请参阅OBJECT_ENTRY_AUTO），](#object_entry_auto)但它不应通过`CoCreateInstance`进行创建。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
