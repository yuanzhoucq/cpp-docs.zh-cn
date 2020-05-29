---
title: CSettingsStoreSP 类
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318456"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 类

该`CSettingsStoreSP`类是一个帮助器类，可用于创建[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)的实例。

## <a name="syntax"></a>语法

```
class CSettingsStoreSP
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSettingsStoreSP：CSettingsStoreSP](#csettingsstoresp)|构造 `CSettingsStoreSP` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSettingsStoreSP：创建](#create)|创建派生自`CSettingsStore`的类的实例。|
|[CSettingsStoreSP：：设置运行时类](#setruntimeclass)|设置运行时类。 该方法`Create`使用运行时类来确定要创建的对象类。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|`m_dwUserData`|存储在对象中的`CSettingsStoreSP`自定义用户数据。 在`CSettingsStoreSP`对象的构造函数中提供此数据。|
|`m_pRegistry`|`Create`方法`CSettingsStore`创建的派生对象。|

## <a name="remarks"></a>备注

可以使用 该`CSettingsStoreSP`类将所有 MFC 注册表操作重定向到其他位置，如 XML 文件或数据库。 为此，请按照下列步骤进行操作：

1. 创建类 （如`CMyStore`），并从 派生`CSettingsStore`它。

1. 将[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)宏与自定义`CSettingsStore`类一起启用动态创建。

1. 重写虚拟函数，并在自定义类`Read`中`Write`实现 和 函数。 实现任何其他功能，将数据读取和写入所需位置。

1. 在应用程序中，调用`CSettingsStoreSP::SetRuntimeClass`并传递指向从类获取的[CRuntimeClass 结构](../../mfc/reference/cruntimeclass-structure.md)的指针。

每当框架通常访问注册表时，它现在都会动态实例化自定义类，并用它来读取或写入数据。

`CSettingsStoreSP::SetRuntimeClass`使用全局静态变量。 因此，一次只能提供一个自定义存储。

## <a name="requirements"></a>要求

**标题：** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP：创建

创建从[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)派生的对象的新实例。

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>参数

*bAdmin*<br/>
[在]确定是否在管理员模式下创建`CSettingsStore`对象的布尔参数。

*b 只读*<br/>
[在]确定是否为只读访问创建`CSettingsStore`对象的布尔参数。

### <a name="return-value"></a>返回值

对新创建`CSettingsStore`对象的引用。

### <a name="remarks"></a>备注

可以使用[方法 CSettingsStoreSP：：SetRuntimeClass](#setruntimeclass)来确定`CSettingsStoreSP::Create`将创建的对象类型。 默认情况下，此方法创建一个`CSettingsStore`对象。

如果在管理员模式下创建`CSettingsStore`对象，则所有注册表访问的默认位置HKEY_LOCAL_MACHINE。 否则，所有注册表访问的默认位置将HKEY_CURRENT_USER。

如果*bAdmin*为 TRUE，则应用程序必须具有管理权限。 否则，当它尝试访问注册表时，它将失败。

### <a name="example"></a>示例

下面的示例演示如何使用`Create``CSettingsStoreSP`类的方法。

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP：CSettingsStoreSP

构造[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)对象。

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*dwUserData*<br/>
[在]`CSettingsStoreSP`对象存储的用户定义数据。

### <a name="remarks"></a>备注

对象`CSettingsStoreSP`将*dwUserData*的数据存储在受保护的成员变量`m_dwUserData`中。

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP：：设置运行时类

设置运行时类。 方法[CSettingsStoreSP：create](#create)使用运行时类来确定要创建的对象类型。

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>参数

*pRTI*<br/>
[在]指向从[CSettingsStore 类](../../mfc/reference/csettingsstore-class.md)派生的类的运行时类信息的指针。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE;如果*pRTI*标识的类不是派生自`CSettingsStore`，则 FALSE

### <a name="remarks"></a>备注

可以使用[CSettingsStoreSP 类](../../mfc/reference/csettingsstoresp-class.md)从`CSettingsStore`派生类。 如果要创建派生`SetRuntimeClass`自`CSettingsStore`的自定义类的对象，请使用 方法。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)
