---
title: "TN039：MFC/OLE 自动化实现 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动化, MFC COM 接口入口点"
  - "IDispatch 接口"
  - "MFC, COM 支持"
  - "MFC, OLE DB 和"
  - "TN039"
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN039：MFC/OLE 自动化实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
## OLE IDispatch 接口概述  
 `IDispatch` 接口是应用程序公开的方法和属性。这样的方法其他应用程序 \(如 Visual Basic，或者任何其他语言，可以利用应用程序的功能。  此接口的最重要部分是 **IDispatch::Invoke** 函数。  MFC 使用计划“映射”实现 **IDispatch::Invoke**。  计划映射在布局或“形状”提供 MFC 实现信息 `CCmdTarget`派生类，这样它可以直接操作对象的属性，或者调用对象内的成员函数满足 **IDispatch::Invoke** 请求。  
  
 在很大程度上，类向导和协作隐藏大多数 MFC OLE 自动化详细信息对程序员的应用程序。  程序员在应用程序集中实际功能公开，因此不必担心基础管道。  
  
 但是，有些情况下之，了解需要哪 MFC 在后台执行。  此注释将寻址框架如何分配 **DISPID**、指向成员函数和属性。  算法使用 MFC 的知识分配的 **DISPID**。仅是必需的，则需要知道 ID 时，例如，当您创建泛“类型库”应用程序的对象时。  
  
## MFC DISPID 分配  
 尽管自动化 \(例如 Visual Basic 用户最终用户，\)，显示启用自动化属性的实际名称和方法在他们的代码 \(如 obj.ShowWindow\)，而 **IDispatch::Invoke** 的实现不接收实际名称。  对于优化原因，它接收 **DISPID**，它是 32 位魔术“Cookie”描述方法或属性进行访问。  这些 **DISPID** 值从 `IDispatch` 实现返回通过其他方法，请调用 **IDispatch::GetIDsOfNames**。  它预期访问每个成员或属性的自动化客户端应用程序调用 `GetIDsOfNames` 一次，并缓存它们供以后对 **IDispatch::Invoke**的调用。  这样，使用大字符串来查找一次每对象只用于完成，而不是一次每调用 **IDispatch::Invoke**。  
  
 基于 MFC 确定两点和属性的 **DISPID**的每个方法：  
  
-   从映射计划 \(1 个相对\) 的顶部的距离。  
  
-   计划映射的距离派生类 \(0 个相对\)  
  
 **DISPID** 分为两部分。  **DISPID** 的 **LOWORD** 包含第一个计划映射组件，从顶部的距离。  **HIWORD** 包含从派生类的距离。  例如：  
  
```  
class CDispPoint : public CCmdTarget  
{  
public:  
    short m_x, m_y;  
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
  
BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)  
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)  
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)  
END_DISPATCH_MAP()  
  
BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)  
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)  
END_DISPATCH_MAP()  
```  
  
 您可以看到，有两类，这些类都公开为 OLE 自动化接口。  这些类之一派生从而利用其他基类的功能，包括为 OLE 自动化部分 \(“X”和“Y”属性中\)。  
  
 MFC 类的 CDispPoint 将生成 **DISPID**。如下：  
  
```  
property X    (DISPID)0x00000001  
property Y    (DISPID)0x00000002  
```  
  
 因为属性不在基类，**DISPID** 的 **HIWORD** 始终为零 \(从派生类的 CDispPoint 的距离为零\)。  
  
 MFC 类的CDisp3DPoint 将生成 **DISPID**。如下：  
  
```  
property Z    (DISPID)0x00000001  
property X    (DISPID)0x00010001  
property Y    (DISPID)0x00010002  
```  
  
 **DISPID** 具有零为 Z "属性的 **HIWORD**，因为在公开属性的类，CDisp3DPoint 定义。  由于 X 和 Y 属性 \(在基类中定义的，而 **DISPID** 的 **HIWORD** 是 1，因此这些属性定义在远处一个从派生类派生的类。  
  
> [!NOTE]
>  **LOWORD** 始终依赖于映射的位置，其中，尽管存在映射中的输入将与显式的 **DISPID** \(请参见下一节有关 `DISP_PROPERTY` 和 `DISP_FUNCTION` 宏的 **\_ID** 生成的信息\)。  
  
## 高级 MFC 调度映射功能  
 具有 ClassWizard 不支持使用此版本的 Visual C\+\+ 中的一些附加功能。  ClassWizard 分别支持定义方法、成员变量的属性和的 get\/set 成员函数的属性，`DISP_FUNCTION`、`DISP_PROPERTY`和 `DISP_PROPERTY_EX`。  这些功能通常是需要创建大多数自动化服务器的所有。  
  
 下面各项宏，在 ClassWizard 支持的宏没有足够时，可以使用：`DISP_PROPERTY_NOTIFY`和 `DISP_PROPERTY_PARAM`。  
  
## DISP\_PROPERTY\_NOTIFY \-宏说明  
  
```  
  
        DISP_PROPERTY_NOTIFY(   
   theClass,   
   pszName,   
   memberName,   
   pfnAfterSet,   
   vtPropType   
)  
```  
  
## 备注  
  
### 参数  
 `theClass`  
 类名。  
  
 `pszName`  
 属性的外部名称。  
  
 `memberName`  
 属性存储于成员变量的名称中。  
  
 `pfnAfterSet`  
 成员函数调用名称属性发生的更改。  
  
 `vtPropType`  
 值指定属性类型。  
  
## 备注  
 此宏十分类似于 `DISP_PROPERTY`，不同之处在于，它接受一个参数。  附加参数，*pfnAfterSet，* 应该没有任何返回不采用参数的成员函数无效，“OnPropertyNotify\(\)”。  **，在** 修改之后，它会调用该成员变量。  
  
## DISP\_PROPERTY\_PARAM \-宏说明  
  
```  
  
        DISP_PROPERTY_PARAM(   
   theClass,  
   pszName,  
   pfnGet,  
   pfnSet,  
   vtPropType,  
   vtsParams   
)  
```  
  
## 备注  
  
### 参数  
 `theClass`  
 类名。  
  
 `pszName`  
 属性的外部名称。  
  
 `memberGet`  
 成员函数名用于获取属性。  
  
 `memberSet`  
 成员函数名用于设置属性。  
  
 `vtPropType`  
 值指定属性类型。  
  
 `vtsParams`  
 空间字符串分隔每个参数的 VTS\_。  
  
## 备注  
 很象 `DISP_PROPERTY_EX` 宏，此宏定义属性的 get 和 set 访问单独成员函数。  此宏，但是，可以为属性指定参数列表。  这对于实现索引或参数化以某种其他方式的属性是很有用的。  参数由属性的新值将始终放置。  例如：  
  
```  
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH,    VTS_I2 VTS_I2)  
```  
  
 将对应获取和设置成员函数：  
  
```  
LPDISPATCH CMyObject::GetItem(short row, short col)  
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)  
```  
  
## DISP\_XXXX\_ID \- 宏说明  
  
```  
  
        DISP_FUNCTION_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnMember,  
   vtRetVal,  
   vtsParams   
) DISP_PROPERTY_ID(   
   theClass,  
   pszName,  
   dispid,  
   memberName,  
   vtPropType   
) DISP_PROPERTY_NOTIFY_ID(   
   theClass,  
   pszName,  
   dispid,  
   memberName,  
   pfnAfterSet,  
   vtPropType   
) DISP_PROPERTY_EX_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnGet,  
   pfnSet,  
   vtPropType   
) DISP_PROPERTY_PARAM_ID(   
   theClass,  
   pszName,  
   dispid,  
   pfnGet,  
   pfnSet,  
   vtPropType,  
   vtsParams   
)  
```  
  
## 备注  
  
### 参数  
 `theClass`  
 类名。  
  
 `pszName`  
 属性的外部名称。  
  
 `dispid`  
 属性或方法的固定的 DISPID。  
  
 `pfnGet`  
 成员函数名用于获取属性。  
  
 `pfnSet`  
 成员函数名用于设置属性。  
  
 `memberName`  
 映射的属性成员变量的名称。  
  
 `vtPropType`  
 值指定属性类型。  
  
 `vtsParams`  
 空间字符串分隔每个参数的 VTS\_。  
  
## 备注  
 这些宏允许将 **DISPID** 指定而不是让 MFC 自动分配一个 IID。  这些高级宏具有相同的名称，只不过 ID 追加到宏名称 \(即  在 `pszName` 参数后面指定的参数确定**DISP\_PROPERTY\_ID**\) 和 ID。  请参见 AFXDISP.H 这些宏有关的更多信息。  **\_ID** 必须将计划映射项的末尾。  这些属性将自动影响的 **DISPID** 生成，与宏**\_ID** 的非版本会类似的方式 \(位置取决于 **DISPID**。\)。  例如：  
  
```  
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)  
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)  
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)  
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)  
END_DISPATCH_MAP()  
```  
  
 MFC 类的CDisp3DPoint 将生成 DISPID。如下：  
  
```  
property X    (DISPID)0x00020003  
property Y    (DISPID)0x00000002  
property Z     (DISPID)0x00000001  
```  
  
 指定固定的 **DISPID** 非常有用维护向后兼容性。以前现有的调度接口，或者为实现特定系统定义的方法或属性 \(通常由负 **DISPID**，如 **DISPID\_NEWENUM** 集合\)。  
  
#### 检索 COleClientItem 的 IDispatch 接口  
 许多服务器以及 OLE 服务器功能外将支持在文档的对象中自动化。  为此自动化接口，为了能够访问直接访问 **COleClientItem::m\_lpObject** 成员变量都是必需的。  下面的代码检索将从 `COleClientItem`派生的对象的 `IDispatch` 接口。  如果必要，查找此功能在应用程序中包含以下代码：  
  
```  
LPDISPATCH CMyClientItem::GetIDispatch()  
{  
    ASSERT_VALID(this);  
    ASSERT(m_lpObject != NULL);  
  
    LPUNKNOWN lpUnk = m_lpObject;  
  
    Run();    // must be running  
  
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
  
 可以直接然后使用从该函数返回的接口或计划附加到 `COleDispatchDriver` 为类型安全访问。  如果直接使用，请确保通过使用指针时调用其 **发布** 成员，在 \( `COleDispatchDriver` 析构函数执行该默认情况\)。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)