---
title: 对象映射宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 73dc924527bac8499adefab3d0d6b51afa500a5a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863153"
---
# <a name="object-map-macros"></a>对象映射宏

这些宏定义对象映射和条目。

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|允许指定类对象的文本说明，该说明将被输入到对象映射中。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|向对象映射中输入 ATL 对象，更新注册表，并创建对象的实例。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

允许你为类对象指定文本说明。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>parameters

*x*<br/>
中类对象的说明。

### <a name="remarks"></a>备注

ATL 通过[OBJECT_ENTRY_AUTO](#object_entry_auto)宏将此说明输入到对象映射。

DECLARE_OBJECT_DESCRIPTION 实现 `GetObjectDescription` 函数，可用于重写[CComCoClass：： GetObjectDescription](ccomcoclass-class.md#getobjectdescription)方法。

`IComponentRegistrar::GetComponents`调用 `GetObjectDescription` 函数。 `IComponentRegistrar` 是一种自动化接口，可用于在 DLL 中注册和注销单个组件。 使用 ATL 项目向导创建组件注册器对象时，向导将自动实现 `IComponentRegistrar` 接口。 `IComponentRegistrar` 通常由 Microsoft 事务服务器使用。

有关 ATL 项目向导的详细信息，请参阅文章[创建 Atl 项目](../../atl/reference/creating-an-atl-project.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

向对象映射中输入 ATL 对象，更新注册表，并创建对象的实例。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>parameters

*clsid*<br/>
中由C++类命名*类*实现的 COM 类的 CLSID。

class<br/>
中实现 clsid 所表示C++的 COM 类的类的名称。

### <a name="remarks"></a>备注

对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。

OBJECT_ENTRY_AUTO 进入 creator 类和类工厂创建者类的函数指针 `CreateInstance` 此对象在自动生成的 ATL 对象映射中的函数。 调用[CAtlComModule：： RegisterServer](catlcommodule-class.md#registerserver)时，它将更新对象映射中每个对象的系统注册表。

下表介绍了如何从给定作为此宏的第二个参数的类中获取添加到对象映射的信息。

|信息|获取自|
|---------------------|-------------------|
|COM 注册|[注册表宏](../../atl/reference/registry-macros.md)|
|类工厂创建|[类工厂宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|实例创建|[聚合宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|组件类别注册|[分类宏](../../atl/reference/category-macros.md)|
|类级别的初始化和清理|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

允许你指定应该注册和初始化对象，但不应可经由 `CoCreateInstance` 在外部创建对象。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>parameters

*clsid*<br/>
中由C++类命名*类*实现的 COM 类的 CLSID。

class<br/>
中实现 clsid 所表示C++的 COM 类的类的名称。

### <a name="remarks"></a>备注

对象项宏置于项目中的全局范围内，以提供对类的注册、初始化和创建的支持。

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 允许你指定应注册和初始化对象（有关详细信息，请参阅[OBJECT_ENTRY_AUTO](#object_entry_auto) ），但它不能通过 `CoCreateInstance`创建。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
