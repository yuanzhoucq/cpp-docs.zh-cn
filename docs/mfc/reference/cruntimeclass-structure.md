---
title: CRuntimeClass 结构
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318550"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 结构

派生自的每个`CObject`类都与一个`CRuntimeClass`结构相关联，可用于在运行时获取有关对象或其基类的信息。

## <a name="syntax"></a>语法

```
struct CRuntimeClass
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRuntime 类：：创建对象](#createobject)|在运行时创建对象。|
|[CRuntime 类：：从名称](#fromname)|使用熟悉的类名称在运行时创建对象。|
|[CRuntime 类：：派生自](#isderivedfrom)|确定类是否派生自指定的类。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CRuntime 类：：m_lpszClassName](#m_lpszclassname)|类的名称。|
|[CRuntime 类：：m_nObjectSize](#m_nobjectsize)|对象大小（以字节为单位）。|
|[CRuntime 类：：m_pBaseClass](#m_pbaseclass)|指向基类`CRuntimeClass`结构的指针。|
|[CRuntime 类：：m_pfnCreateObject](#m_pfncreateobject)|指向动态创建对象的函数的指针。|
|[CRuntime 类：：m_pfnGetBaseClass](#m_pfngetbaseclass)|返回`CRuntimeClass`结构（仅在动态链接时可用）。|
|[CRuntime 类：：m_wSchema](#m_wschema)|类的架构编号。|

## <a name="remarks"></a>备注

`CRuntimeClass`是一个结构，因此没有基类。

当需要对函数参数进行额外的类型检查时，或者在必须基于对象的类编写特殊用途代码时，在运行时确定对象类的能力非常有用。 C++ 语言不直接支持运行时类信息。

`CRuntimeClass`提供有关相关C++对象的信息，例如指向基类`CRuntimeClass`的指针和相关类的 ASCII 类名称。 此结构还实现各种函数，这些函数可用于动态创建对象、使用熟悉的名称指定对象类型，并确定相关类是否派生自特定类。

有关 使用`CRuntimeClass`的详细信息，请参阅[访问运行时类信息](../../mfc/accessing-run-time-class-information.md)的文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CRuntimeClass`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntime 类：：创建对象

调用此函数以在运行时动态创建指定的类。

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>参数

*lpszClass名称*<br/>
要创建的类的熟悉名称。

### <a name="return-value"></a>返回值

指向新创建的对象的指针，或者 NULL（如果未找到类名称或内存不足以创建对象）。

### <a name="remarks"></a>备注

派生自的`CObject`类可以支持动态创建，即在运行时创建指定类的对象的能力。 例如，文档、视图和框架类应支持动态创建。 有关动态创建和`CreateObject`成员的详细信息，请参阅[CObject 类](../../mfc/using-cobject.md)和[CObject 类：指定功能级别](../../mfc/specifying-levels-of-functionality.md)。

### <a name="example"></a>示例

  请参阅["从派生"](#isderivedfrom)的示例。

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntime 类：：从名称

调用此函数以检索与`CRuntimeClass`熟悉名称关联的结构。

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>参数

*lpszClass名称*<br/>
派生自`CObject`的类的熟悉名称。

### <a name="return-value"></a>返回值

指向`CRuntimeClass`对象的指针，对应于*在 lpszClassName*中传递的名称。 如果未找到匹配的类名称，则函数返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntime 类：：派生自

调用此函数以确定调用类是否派生自*pBaseClass 参数*中指定的类。

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>参数

*pBase 类*<br/>
派生自`CObject`的类的熟悉名称。

### <a name="return-value"></a>返回值

如果类调用`IsDerivedFrom`派生自其`CRuntimeClass`结构为参数的基类，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

关系由成员的类"行走"到派生类链一直"走"到顶部来确定。 仅当找不到基类的匹配项时，此功能才会返回 FALSE。

> [!NOTE]
> 若要使用结构`CRuntimeClass`，必须在要检索运行时对象的类的实现中包括IMPLEMENT_DYNAMIC、IMPLEMENT_DYNCREATE或IMPLEMENT_SERIAL宏。

有关使用`CRuntimeClass`的详细信息，请参阅文章[CObject 类：访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntime 类：：m_lpszClassName

包含 ASCII 类名称的 null 端接字符串。

### <a name="remarks"></a>备注

此名称可用于使用成员函数创建类的`FromName`实例。

### <a name="example"></a>示例

  请参阅["从派生"](#isderivedfrom)的示例。

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntime 类：：m_nObjectSize

对象的大小（以字节为单位）。

### <a name="remarks"></a>备注

如果对象具有指向已分配内存的数据成员，则不包括该内存的大小。

### <a name="example"></a>示例

  请参阅["从派生"](#isderivedfrom)的示例。

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntime 类：：m_pBaseClass

如果应用程序以静态方式链接到 MFC，则此数据成员包含指向基类`CRuntimeClass`结构的指针。

### <a name="remarks"></a>备注

如果应用程序动态链接到 MFC 库，请参阅[m_pfnGetBaseClass](#m_pfngetbaseclass)。

### <a name="example"></a>示例

  请参阅["从派生"](#isderivedfrom)的示例。

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntime 类：：m_pfnCreateObject

指向创建类对象的默认构造函数的函数指针。

### <a name="remarks"></a>备注

仅当类支持动态创建时，此指针才有效;否则，函数将返回 NULL。

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntime 类：：m_pfnGetBaseClass

如果应用程序使用 MFC 库作为共享 DLL，则此数据成员指向返回基类`CRuntimeClass`结构的函数。

### <a name="remarks"></a>备注

如果应用程序静态链接到 MFC 库，请参阅[m_pBaseClass](#m_pbaseclass)。

### <a name="example"></a>示例

  请参阅["从派生"](#isderivedfrom)的示例。

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntime 类：：m_wSchema

架构编号 （-1 表示不可序列化类）。

### <a name="remarks"></a>备注

有关架构编号的详细信息，请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>示例

  请参阅["从派生"](#isderivedfrom)的示例。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CObject：获取运行时类](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[对象：：是](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
