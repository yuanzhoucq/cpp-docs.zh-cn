---
title: 'TN039: MFC OLE 自动化实现 |Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59eca912aab816f75ce8d585036f8f900c4f7bd3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399868"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039：MFC/OLE 自动化实现

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

## <a name="overview-of-ole-idispatch-interface"></a>OLE IDispatch 接口的概述

`IDispatch`接口是依据应用程序公开的方法和属性，如此一来，其他应用程序，如 Visual BASIC 或其他语言，可使用应用程序的功能的方式。 此接口的最重要部分是`IDispatch::Invoke`函数。 MFC 使用"调度映射"来实现`IDispatch::Invoke`。 调度映射上的布局或"形状"提供的 MFC 实现信息你`CCmdTarget`的派生类中，以便它可以直接操作对象的属性或调用成员函数内您的对象以满足`IDispatch::Invoke`请求数。

大多数情况下，ClassWizard 和 MFC 共同协作以隐藏大部分的应用程序程序员的 OLE 自动化的详细信息。 程序员重点介绍用于公开应用程序中的实际功能，无需担心基础的基本功能。

有的情况下，但是，必须先了解 MFC 在后台执行的操作。 本说明将解决框架如何分配**DISPID**的成员函数和属性。 MFC 使用的分配的算法的知识**DISPID**s 才是必需时需要了解的 Id，例如当您创建的"类型库"的应用程序的对象。

## <a name="mfc-dispid-assignment"></a>MFC DISPID 分配

尽管自动化 （Visual Basic 用户，例如），最终用户看到的实际名称的属性和方法在其代码 （如目标启用自动化ShowWindow)，实现`IDispatch::Invoke`不会接收的实际名称。 为了优化，它接收**DISPID**，这是一个 32 位"神奇的 cookie"描述的方法或要访问的属性。 这些**DISPID**值返回从`IDispatch`实现通过另一种方法，名为`IDispatch::GetIDsOfNames`。 自动化客户端应用程序将调用`GetIDsOfNames`后它要为每个成员或属性访问，并缓存到更高版本调用`IDispatch::Invoke`。 这样一来，成本高昂的字符串查找只进行一次每次对象使用，而不是一次每个`IDispatch::Invoke`调用。

MFC 确定**DISPID**为每个方法和属性基于两件事：

- 从顶部的调度映射 （1 相关） 的距离

- 调度映射从派生程度最高的类 (0 相对) 的距离

**DISPID**分为两个部分。 **使用 LOWORD**的**DISPID**包含第一个组件，从调度映射的顶部的距离。 **HIWORD**包含从派生程度最高的类之间的距离。 例如：

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

如您所见，有两个类，这两种公开 OLE 自动化接口。 这些类之一派生自另并因此使用基类的功能，包括 OLE 自动化过程 ("x"和"y"属性在此情况下)。

MFC 将生成**DISPID**s 类 CDispPoint，如下所示：

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

因为属性不在基类**HIWORD**的**DISPID**值始终为零 （从 CDispPoint 的派生程度最高类之间的距离为零）。

MFC 将生成**DISPID**s 类 CDisp3DPoint，如下所示：

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Z 属性赋**DISPID**带零**HIWORD**由于它公开的属性，CDisp3DPoint 类中定义。 由于基类中定义的 X 和 Y 属性**HIWORD**的**DISPID**为 1，因为这些属性定义的类是在从派生程度最高的类的一个派生的距离。

> [!NOTE]
> **使用 LOWORD**始终确定按位置在映射中，即使存在与显式映射中的条目**DISPID** (参阅下一步部分信息 **_ID**新版`DISP_PROPERTY`和`DISP_FUNCTION`宏)。

## <a name="advanced-mfc-dispatch-map-features"></a>高级 MFC 调度映射功能

有很多其他功能，ClassWizard 不支持此版本的 Visual c + +。 支持 ClassWizard `DISP_FUNCTION`， `DISP_PROPERTY`，和`DISP_PROPERTY_EX`用于定义应用程序的方法、 成员变量属性和 get/set 成员函数属性，分别。 这些功能通常所创建大多数自动化服务器所需的所有内容。

支持的 ClassWizard 宏不足够时，可以使用以下其他宏： `DISP_PROPERTY_NOTIFY`，和`DISP_PROPERTY_PARAM`。

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY-宏说明

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*成员名称*<br/>
在其中存储属性的成员变量的名称。

*pfnAfterSet*<br/>
更改属性时要调用的成员函数的名称。

*vtPropType*<br/>
一个指定属性的类型值。

### <a name="remarks"></a>备注

此宏非常类似 DISP_PROPERTY，只不过它接受一个附加参数。 其他参数， *pfnAfterSet，* 应为不返回任何内容并不带任何参数，void OnPropertyNotify() 的成员函数。 它将叫做**后**成员变量已被修改。

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM-宏说明

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*memberGet*<br/>
用来获取属性的成员函数的名称。

*成员集*<br/>
用于设置属性的成员函数的名称。

*vtPropType*<br/>
一个指定属性的类型值。

*vtsParams*<br/>
分隔 VTS_ 空间构成的字符串，每个参数。

### <a name="remarks"></a>备注

更像 DISP_PROPERTY_EX 宏，此宏可定义与单独的 Get 和 Set 成员函数访问的属性。 此宏，但是，可以指定属性的参数列表。 这可用于以某种其他方式实现的索引或参数化属性。 参数将始终放在最前面后, 跟该属性的新值。 例如：

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

将对应于 get 和 set 成员函数：

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID-宏说明

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>参数

*类*<br/>
类的名称。

*pszName*<br/>
属性的外部名称。

*dispid*<br/>
固定的属性或方法的 DISPID。

*pfnGet*<br/>
用来获取属性的成员函数的名称。

*pfnSet*<br/>
用于设置属性的成员函数的名称。

*成员名称*<br/>
要映射到属性的成员变量的名称

*vtPropType*<br/>
一个指定属性的类型值。

*vtsParams*<br/>
分隔 VTS_ 空间构成的字符串，每个参数。

### <a name="remarks"></a>备注

这些宏，可以指定**DISPID**而不是由 MFC 自动分配一个。 这些高级宏具有相同的名称，但该 ID 追加到宏名称 (例如**DISP_PROPERTY_ID**) 和 ID 由后指定的参数*pszName*参数。 请参阅 AFXDISP。H 表示这些宏的详细信息。 **_ID**条目必须放在调度映射的末尾。 它们会影响自动**DISPID**作为非相同的方式生成 **_ID**宏的版本将 ( **DISPID**s 由位置)。 例如：

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC 将生成 Dispid CDisp3DPoint 类，如下所示：

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

指定的固定**DISPID**可将保持向后兼容到以前就存在的调度接口，或实现某些系统定义的方法或属性 (通常由负**DISPID**，如**DISPID_NEWENUM**集合)。

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>检索 COleClientItem IDispatch 接口

许多服务器将支持其文档对象，以及 OLE 服务器功能的自动化功能。 若要访问此自动化接口，则有必要进行直接访问`COleClientItem::m_lpObject`成员变量。 下面的代码将检索`IDispatch`接口的一个派生自`COleClientItem`。 如果找到此功能有必要，您可以在应用程序中包括下面的代码：

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

调度接口返回的此函数无法然后直接使用或附加到`COleDispatchDriver`为类型安全的访问。 如果直接使用，请确保您调用其`Release`成员时通过使用指针 (`COleDispatchDriver`析构函数执行此默认情况下)。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
