---
title: 'TN039: MFC OLE 自动化实现 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 0c6475e8c259026618192489ac2c67c20ed03d92
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385334"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039：MFC/OLE 自动化实现
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
## <a name="overview-of-ole-idispatch-interface"></a>OLE IDispatch 接口的概述  
 `IDispatch`接口是依据应用程序公开的应用程序的功能，可以进行其他应用程序，如 Visual BASIC 或其他语言，以便使用方法和属性的方法。 此接口的最重要部分是**idispatch:: Invoke**函数。 MFC 使用"调度映射"实现**idispatch:: Invoke**。 调度映射提供的 MFC 实现信息的布局或"shape"的有关你`CCmdTarget`-派生类中，以便它可以直接操作的对象的属性或调用成员函数中你的对象，以满足**Idispatch:: Invoke**请求。  
  
 大多数情况下，ClassWizard 和 MFC 共同协作以隐藏大部分的应用程序程序员的 OLE 自动化的详细信息。 程序员重点介绍在应用程序中公开的实际功能，无需担心基础的管道。  
  
 有的情况下，但是，十分了解 MFC 在后台执行的操作所必需。 本说明将地址如何分配 framework **DISPID**s 对成员函数和属性。 MFC 使用分配的算法的知识**DISPID**s 才有必要，您需要知道的 Id，例如当你创建的"类型库"为应用程序的对象。  
  
## <a name="mfc-dispid-assignment"></a>MFC DISPID 分配  
 尽管自动化 （Visual Basic 用户，例如），最终用户看到的实际名称自动化启用属性和方法在其代码 （如 obj。ShowWindow) 的实现**idispatch:: Invoke**不会收到的实际名称。 为了优化，它接收**DISPID**，这是一个 32 位"幻 cookie"，其中描述的方法或属性访问。 这些**DISPID**从返回值`IDispatch`通过调用另一个方法的实现**IDispatch::GetIDsOfNames**。 自动化客户端应用程序将调用`GetIDsOfNames`后它想为每个成员或属性来访问，并缓存它们以便更高版本调用**idispatch:: Invoke**。 这样一来，昂贵字符串查找仅执行一次每个对象使用，而不是一次每个**idispatch:: Invoke**调用。  
  
 MFC 确定**DISPID**为每个方法和属性基于以下两项操作：  
  
-   调度映射 （1 相对） 的顶部距离  
  
-   从最多衍生的类 (0 相对) 的调度映射的距离  
  
 **DISPID**分为两个部分。 **LOWORD**的**DISPID**包含第一个组件，按自上而下的调度映射的距离。 **HIWORD**包含最多衍生的类之间的距离。 例如：  
  
```  
class CDispPoint : public CCmdTarget  
{  
public:  
    short m_x,
    m_y;  
 ...  
    DECLARE_DISPATCH_MAP() 
 ...  
};  
 
class CDisp3DPoint : public CDispPoint  
{  
public:  
    short m_z;  
 ...  
    DECLARE_DISPATCH_MAP() 
 ...  
};  
 
BEGIN_DISPATCH_MAP(CDispPoint,
    CCmdTarget)  
    DISP_PROPERTY(CDispPoint, "x",
    m_x,
    VT_I2)  
    DISP_PROPERTY(CDispPoint, "y",
    m_y,
    VT_I2)  
END_DISPATCH_MAP()  
 
BEGIN_DISPATCH_MAP(CDisp3DPoint,
    CDispPoint)  
    DISP_PROPERTY(CDisp3DPoint, "z",
    m_z,
    VT_I2)  
END_DISPATCH_MAP()  
```  
  
 如你所见，有两个类，这两种公开 OLE 自动化接口。 这些类之一派生自另，并因此利用基类的功能，包括 OLE 自动化一部分 ("x"和"y"在此情况下的属性)。  
  
 MFC 将生成**DISPID**s 针对类 CDispPoint，如下所示：  
  
```  
property X    (DISPID)0x00000001  
property Y    (DISPID)0x00000002  
```  
  
 由于属性不是在基的类中， **HIWORD**的**DISPID**值始终为零 （CDispPoint 的派生程度最高类之间的距离为零）。  
  
 MFC 将生成**DISPID**s 针对类 CDisp3DPoint，如下所示：  
  
```  
property Z    (DISPID)0x00000001  
property X    (DISPID)0x00010001  
property Y    (DISPID)0x00010002  
```  
  
 给定的 Z 属性**DISPID**带零**HIWORD**由于它公开的属性，CDisp3DPoint 的类中定义。 由于在基类中定义的 X 和 Y 属性**HIWORD**的**DISPID**是 1，因为在其中定义这些属性的类是在从派生程度最高的类的一个派生的距离。  
  
> [!NOTE]
>  **LOWORD**始终由的位置的映射中，即使存在具有显式映射中的条目**DISPID** (参阅下一步部分信息 **_ID**版本的`DISP_PROPERTY`和`DISP_FUNCTION`宏)。  
  
## <a name="advanced-mfc-dispatch-map-features"></a>高级 MFC 调度映射功能  
 有大量 ClassWizard 不支持的其他功能对于此版本的 Visual c + +。 ClassWizard 支持`DISP_FUNCTION`， `DISP_PROPERTY`，和`DISP_PROPERTY_EX`用于定义应用程序的方法，成员变量属性和 get/set 成员函数属性，分别。 这些功能通常是创建大多数自动化服务器所需的所有。  
  
 没有足够的 ClassWizard 支持宏时，可以使用以下其他宏： `DISP_PROPERTY_NOTIFY`，和`DISP_PROPERTY_PARAM`。  
  
## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY-宏说明  
  
```  
 
    DISP_PROPERTY_NOTIFY(
 theClass,   
    pszName, 
    memberName, 
    pfnAfterSet, 
    vtPropType) 
```  
  
## <a name="remarks"></a>备注  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 属性的外部名称。  
  
 `memberName`  
 在其中存储属性的成员变量的名称。  
  
 `pfnAfterSet`  
 属性更改时要调用的成员函数的名称。  
  
 `vtPropType`  
 指定属性的类型的值。  
  
## <a name="remarks"></a>备注  
 此宏非常类似于`DISP_PROPERTY`，只不过它接受一个额外的参数。 这个附加参数， *pfnAfterSet，* 应会返回任何内容并没有采用任何参数 void OnPropertyNotify() 的成员函数。 它将调用**后**成员变量已被修改。  
  
## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM-宏说明  
  
```  
 
    DISP_PROPERTY_PARAM(
 theClass,   
    pszName, 
    pfnGet, 
    pfnSet, 
    vtPropType, 
    vtsParams) 
```  
  
## <a name="remarks"></a>备注  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 属性的外部名称。  
  
 `memberGet`  
 用来获取属性的成员函数的名称。  
  
 `memberSet`  
 用于设置属性的成员函数的名称。  
  
 `vtPropType`  
 指定属性的类型的值。  
  
 `vtsParams`  
 空间的字符串分隔 VTS_ 每个参数。  
  
## <a name="remarks"></a>备注  
 非常类似`DISP_PROPERTY_EX`宏，此宏定义与单独的 Get 和 Set 成员函数访问的属性。 此宏，但是，可以指定参数列表的属性。 这可用于以某种其他方式实现索引或参数化的属性。 参数将始终放置首先，跟属性的新值。 例如：  
  
```  
DISP_PROPERTY_PARAM(CMyObject, "item",
    GetItem,
    SetItem,
    VT_DISPATCH,
    VTS_I2 VTS_I2)  
```  
  
 将对应获取和设置成员函数：  
  
```  
LPDISPATCH CMyObject::GetItem(short row,
    short col)  
void CMyObject::SetItem(short row,
    short col,
    LPDISPATCH newValue)  
```  
  
## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID-宏说明  
  
```  
 
    DISP_FUNCTION_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnMember, 
    vtRetVal, 
    vtsParams)DISP_PROPERTY_ID(
 theClass,   
    pszName, 
    dispid, 
    memberName, 
    vtPropType)DISP_PROPERTY_NOTIFY_ID(
 theClass,   
    pszName, 
    dispid, 
    memberName, 
    pfnAfterSet, 
    vtPropType)DISP_PROPERTY_EX_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnGet, 
    pfnSet, 
    vtPropType)DISP_PROPERTY_PARAM_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnGet, 
    pfnSet, 
    vtPropType, 
    vtsParams) 
```  
  
## <a name="remarks"></a>备注  
  
### <a name="parameters"></a>参数  
 `theClass`  
 类的名称。  
  
 `pszName`  
 属性的外部名称。  
  
 `dispid`  
 固定的 DISPID，为属性或方法。  
  
 `pfnGet`  
 用来获取属性的成员函数的名称。  
  
 `pfnSet`  
 用于设置属性的成员函数的名称。  
  
 `memberName`  
 要映射到的属性成员变量的名称  
  
 `vtPropType`  
 指定属性的类型的值。  
  
 `vtsParams`  
 空间的字符串分隔 VTS_ 每个参数。  
  
## <a name="remarks"></a>备注  
 这些宏可用于指定**DISPID**而不是由 MFC 自动分配一个。 这些高级宏具有相同的名称，但该 ID 追加到宏名称 (例如**DISP_PROPERTY_ID**) 和 ID 由紧后面指定的参数`pszName`参数。 请参阅 AFXDISP。有关这些宏的详细信息的 H。 **_ID**条目必须放置在调度映射的末尾。 其影响自动**DISPID**方式与非相同的生成 **_ID**版本宏将 ( **DISPID**s 由位置)。 例如：  
  
```  
BEGIN_DISPATCH_MAP(CDisp3DPoint,
    CCmdTarget)  
    DISP_PROPERTY(CDisp3DPoint, "y",
    m_y,
    VT_I2)  
    DISP_PROPERTY(CDisp3DPoint, "z",
    m_z,
    VT_I2)  
    DISP_PROPERTY_ID(CDisp3DPoint, "x",
    0x00020003,
    m_x,
    VT_I2)  
END_DISPATCH_MAP()  
```  
  
 MFC 将生成 Dispid 类 CDisp3DPoint，如下所示：  
  
```  
property X    (DISPID)0x00020003  
property Y    (DISPID)0x00000002  
property Z     (DISPID)0x00000001  
```  
  
 指定固定**DISPID**可将保持向后兼容到先前存在的调度接口，或实现某些系统定义的方法或属性 (通常由一个负数**DISPID**，如**DISPID_NEWENUM**集合)。  
  
#### <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>检索 COleClientItem IDispatch 接口  
 许多服务器将支持及其文档对象，以及 OLE 服务器功能的自动化功能。 若要获得此自动化接口的访问权限，则有必要进行直接访问**COleClientItem::m_lpObject**成员变量。 下面的代码将检索`IDispatch`接口的对象派生自`COleClientItem`。 如果找到此功能需要，您可以在你的应用程序中包括下面的代码：  
  
```  
LPDISPATCH CMyClientItem::GetIDispatch()  
{  
    ASSERT_VALID(this);

 ASSERT(m_lpObject != NULL);

 
    LPUNKNOWN lpUnk = m_lpObject;  
 
    Run();
*// must be running  
 
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
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch)   
 != NOERROR)  
 {  
    TRACE0("Warning: does not support IDispatch!\n");

    return NULL;  
 }  
 
    ASSERT(lpDispatch != NULL);

    return lpDispatch;  
}  
```  
  
 调度接口返回的此函数无法然后直接使用或附加到`COleDispatchDriver`为类型安全的访问。 如果直接使用，请确保你调用其**版本**成员时通过使用指针 (`COleDispatchDriver`析构函数执行此默认情况下)。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

