---
title: 事件映射
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: c79d2fb1ac73947ddb13adcbd444ff7b5d50bdb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365741"
---
# <a name="event-maps"></a>事件映射

每当控件希望通知其容器一些操作（由控件开发人员确定）已发生（如键击、鼠标单击或对控件状态的更改）时，它将调用事件触发函数。 此函数通过触发相关事件通知控件容器一些重要的操作已发生。

Microsoft 基础类库提供了针对触发事件而优化的编程模型。 在此模型中，“事件映射”用于为特殊控件指定哪些函数触发哪些事件。 事件映射包含每个事件的一个宏。 例如，触发常用 Click 事件的事件映射可能与下类似：

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

宏`EVENT_STOCK_CLICK`指示控件每次检测到鼠标单击时都会触发库存单击事件。 有关其他股票事件的更详细列表，请参阅[文章 ActiveX 控件：事件](../../mfc/mfc-activex-controls-events.md)。 宏还可用于指示自定义事件。

虽然事件映射宏很重要，但您一般不会直接插入这些宏。 这是因为**属性**窗口（**在类视图中**）在使用该窗口将事件触发函数与事件关联时，会自动在源文件中创建事件映射条目。 任何时候要编辑或添加事件映射条目时，都可以使用 **"属性"** 窗口。

为了支持事件映射，MFC 提供了下列宏：

## <a name="event-map-macros"></a>事件映射宏

### <a name="event-map-declaration-and-demarcation"></a>事件映射声明和划分

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|声明事件映射将在类中用于将事件映射到事件触发函数（必须在类声明中使用）。|
|[BEGIN_EVENT_MAP](#begin_event_map)|开始事件映射的定义（必须在类实现中使用）。|
|[END_EVENT_MAP](#end_event_map)|结束事件映射的定义（必须在类实现中使用）。|

### <a name="event-mapping-macros"></a>事件映射宏

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|指示将触发指定事件的事件触发函数。|
|[EVENT_CUSTOM_ID](#event_custom_id)|使用指定调度 ID 指示将触发指定事件的事件触发函数。|

### <a name="message-mapping-macros"></a>消息映射宏

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|指示 OLE 控件处理的自定义谓词。|
|[ON_STDOLEVERB](#on_stdoleverb)|重写 OLE 控件的标准谓词映射。|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

程序中`COleControl`的每个派生类都可以提供事件映射来指定控件将触发的事件。

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>备注

在类声明末尾使用DECLARE_EVENT_MAP宏。 然后，在定义类成员函数的 .cpp 文件中，使用BEGIN_EVENT_MAP个宏、每个控件事件的宏条目和END_EVENT_MAP宏来声明事件列表的结束。

有关事件映射的详细信息，请参阅["ActiveX 控件：事件](../../mfc/mfc-activex-controls-events.md)"一文。

### <a name="requirements"></a>要求

**头**afxctl.h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

开始定义事件映射。

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>参数

*类*<br/>
指定事件映射为其事件映射的控件类的名称。

*基类*<br/>
指定*类*的基类的名称。

### <a name="remarks"></a>备注

在定义类成员函数的实现 （.cpp） 文件中，使用BEGIN_EVENT_MAP宏启动事件映射，然后为每个事件添加宏条目，然后使用END_EVENT_MAP宏完成事件映射。

有关事件映射和BEGIN_EVENT_MAP宏的详细信息，请参阅[文章 ActiveX 控件：事件](../../mfc/mfc-activex-controls-events.md)。

### <a name="requirements"></a>要求

**头**afxctl.h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

使用END_EVENT_MAP宏结束事件映射的定义。

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>要求

**头**afxctl.h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

为自定义事件定义事件映射条目。

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>参数

*pszName*<br/>
事件的名称。

*普芬火*<br/>
事件触发函数的名称。

*vtsParams*<br/>
指定函数参数列表的一个或多个常量的空间分隔列表。

### <a name="remarks"></a>备注

*vtsParams*参数是一个空间分隔的值列表，`VTS_`与常量。 一个或多个这些值由空格（不是逗号）分隔，指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定包含表示 RGB 颜色值的 32 位整数的列表，后跟指向 OLE`IFontDisp`字体对象接口的指针。

常`VTS_`量及其含义如下：

|符号|参数类型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**长**|
|VTS_R4|**浮动**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|货币|
|VTS_DATE|DATE|
|VTS_BSTR|**康斯特**__字符\*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|句柄|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> 已为所有变体类型定义了其他变体常量，但提供指向变体数据常量的VTS_FONT和VTS_PICTURE除外。 这些常量使用约定`VTS_Pconstantname`命名。 例如，VTS_PCOLOR是指向VTS_COLOR常量的指针。

### <a name="requirements"></a>要求

**头**afxctl.h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

为属于*dispid*指定的调度 ID 的自定义事件定义事件触发函数。

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>参数

*pszName*<br/>
事件的名称。

*不一部分*<br/>
控件在触发事件时使用的调度 ID。

*普芬火*<br/>
事件触发函数的名称。

*vtsParams*<br/>
触发事件时传递给控制容器的参数的可变列表。

### <a name="remarks"></a>备注

*vtsParams*参数是空格分隔的值列表和`VTS_`常量。 由空格（而不是逗号）分隔的一个或多个值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定包含表示 RGB 颜色值的 32 位整数的列表，后跟指向 OLE`IFontDisp`字体对象接口的指针。

有关常量的列表，`VTS_`请参阅[EVENT_CUSTOM](#event_custom)。

### <a name="requirements"></a>要求

**头**afxctl.h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

此宏定义一个消息映射条目，该条目将自定义谓词映射到控件的特定成员函数。

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>参数

*idsVerbName*<br/>
谓词名称的字符串资源 ID。

*成员Fxn*<br/>
框架在调用谓词时调用的函数。

### <a name="remarks"></a>备注

资源编辑器可用于创建添加到字符串表的自定义谓词名称。

*成员Fxn*的功能原型是：

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

lpMsg、hWndParent*hWndParent*和*lpRect*参数的值取自`IOleObject::DoVerb`成员函数的相应参数。 *lpMsg*

### <a name="requirements"></a>要求

**头**afxole.h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

使用此宏重写标准谓词的默认行为。

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>参数

*iVerb*<br/>
重写谓词的标准谓词索引。

*成员Fxn*<br/>
框架在调用谓词时调用的函数。

### <a name="remarks"></a>备注

标准动词索引是形式`OLEIVERB_`，后跟一个动作。 OLEIVERB_SHOW、OLEIVERB_HIDE和OLEIVERB_UIACTIVATE是标准动词的一些示例。

有关用作*成员Fxn*参数的功能原型的说明，请参阅[ON_OLEVERB。](#on_oleverb)

### <a name="requirements"></a>要求

**头**afxole.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
