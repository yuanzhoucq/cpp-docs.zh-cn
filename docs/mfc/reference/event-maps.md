---
title: 事件映射 |Microsoft 文档
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce997441c11287626e9681a661f858e33ccdde24
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322207"
---
# <a name="event-maps"></a>事件映射

每当控件希望通知其容器一些操作（由控件开发人员确定）已发生（如键击、鼠标单击或对控件状态的更改）时，它将调用事件触发函数。 此函数通过触发相关事件通知控件容器一些重要的操作已发生。

Microsoft 基础类库提供了针对触发事件而优化的编程模型。 在此模型中，“事件映射”用于为特殊控件指定哪些函数触发哪些事件。 事件映射包含每个事件的一个宏。 例如，触发常用 Click 事件的事件映射可能与下类似：

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK`宏指示控件将触发常用 Click 事件每次检测到鼠标单击。 其他常用事件的更详细的列表，请参阅文章[ActiveX 控件： 事件](../../mfc/mfc-activex-controls-events.md)。 宏还可用于指示自定义事件。

虽然事件映射宏很重要，但您一般不会直接插入这些宏。 这是因为“属性”窗口将在您将其用于将事件触发函数与事件关联时，自动在源文件中创建时间映射条目。 每当您需要编辑或添加事件映射条目时，均可使用“属性”窗口。

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

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

每个`COleControl`-程序中的派生的类可提供事件映射来指定控件将激发的事件。

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>备注

使用`DECLARE_EVENT_MAP`宏在类声明的末尾。 然后，在定义类的成员函数的.cpp 文件，使用`BEGIN_EVENT_MAP`宏，为每个控件的事件，宏项和`END_EVENT_MAP`宏来声明事件列表的末尾。

事件映射的详细信息，请参阅文章[ActiveX 控件： 事件](../../mfc/mfc-activex-controls-events.md)。

### <a name="requirements"></a>要求

**标头**afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

开始事件映射的定义。

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>参数

*类*  
指定其事件将此项映射的控件类的名称。

*baseClass*  
指定的基类的名称*类*。

### <a name="remarks"></a>备注

在实现 (.cpp) 文件中定义你的类的成员函数，开始对事件地图`BEGIN_EVENT_MAP`宏，然后为每个事件，添加宏条目并完成对事件地图`END_EVENT_MAP`宏。

有关事件的详细信息图和`BEGIN_EVENT_MAP`宏，请参阅文章[ActiveX 控件： 事件](../../mfc/mfc-activex-controls-events.md)。

### <a name="requirements"></a>要求

**标头**afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

使用`END_EVENT_MAP`宏结束事件映射的定义。

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>要求

**标头**afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM

定义自定义事件的事件映射条目。

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>参数

*pszName*  
事件的名称。

*pfnFire*  
事件触发函数的名称。

*vtsParams*  
指定函数的参数列表的一个或多个常量的以空格分隔的列表。

### <a name="remarks"></a>备注

*VtsParams*参数是以空格分隔的值列表`VTS_`常量。 一个或多个用空格 （而不是逗号） 分隔这些值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定列表包含一个 32 位整型，表示 RGB 颜色值后, 跟的指针到`IFontDisp`OLE 字体对象接口。

`VTS_`常量和它们的含义如下：

|符号|参数类型|
|------------|--------------------|
|`VTS_I2`|**short**|
|`VTS_I4`|**long**|
|`VTS_R4`|**float**|
|`VTS_R8`|**double**|
|`VTS_COLOR`|`OLE_COLOR`|
|`VTS_CY`|`CURRENCY`|
|`VTS_DATE`|`DATE`|
|`VTS_BSTR`|**const** __char\*__|
|`VTS_DISPATCH`|`LPDISPATCH`|
|`VTS_FONT`|`IFontDispatch*`|
|`VTS_HANDLE`|`HANDLE`|
|`VTS_SCODE`|`SCODE`|
|`VTS_BOOL`|`BOOL`|
|`VTS_VARIANT`|`const VARIANT*`|
|`VTS_PVARIANT`|`VARIANT*`|
|`VTS_UNKNOWN`|`LPUNKNOWN`|
|`VTS_OPTEXCLUSIVE`|`OLE_OPTEXCLUSIVE`|
|`VTS_PICTURE`|`IPictureDisp*`|
|`VTS_TRISTATE`|`OLE_TRISTATE`|
|`VTS_XPOS_PIXELS`|`OLE_XPOS_PIXELS`|
|`VTS_YPOS_PIXELS`|`OLE_YPOS_PIXELS`|
|`VTS_XSIZE_PIXELS`|`OLE_XSIZE_PIXELS`|
|`VTS_YSIZE_PIXELS`|`OLE_YSIZE_PIXELS`|
|`VTS_XPOS_HIMETRIC`|`OLE_XPOS_HIMETRIC`|
|`VTS_YPOS_HIMETRIC`|`OLE_YPOS_HIMETRIC`|
|`VTS_XSIZE_HIMETRIC`|`OLE_XSIZE_HIMETRIC`|
|`VTS_YSIZE_HIMETRIC`|`OLE_YSIZE_HIMETRIC`|

> [!NOTE]
> 为所有变体类型，除定义其他变体常量`VTS_FONT`和`VTS_PICTURE`，提供指向各种不同的数据常量的指针。 使用命名这些常量`VTS_Pconstantname`约定。 例如，`VTS_PCOLOR`是一个指向`VTS_COLOR`常量。

### <a name="requirements"></a>要求

**标头**afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

定义事件触发函数的自定义事件属于通过指定的调度 ID *dispid*。

```cpp
EVENT_CUSTOM_ID(
  pszName,
  dispid,
  pfnFire,
  vtsParams)
```

### <a name="parameters"></a>参数

*pszName*  
事件的名称。

*dispid*  
使用控件时激发该事件的调度 ID。

*pfnFire*  
事件触发函数的名称。

*vtsParams*  
激发事件时，变量参数的列表传递给控件容器。

### <a name="remarks"></a>备注

*VtsParams*自变量是空格分隔的值从列表`VTS_`常量。 一个或多个由空格分隔，而不是逗号，这些值指定函数的参数列表。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定列表包含一个 32 位整型，表示 RGB 颜色值后, 跟的指针到`IFontDisp`OLE 字体对象接口。

有关的列表`VTS_`常量，请参阅[EVENT_CUSTOM](#event_custom)。

### <a name="requirements"></a>要求

**标头**afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

此宏定义一个映射到您的控件的特定成员函数的自定义的谓词的消息映射条目。

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>参数

*idsVerbName*谓词的名称的字符串资源 ID。

*f x n*  
框架在调用谓词时调用的函数。

### <a name="remarks"></a>备注

资源编辑器可以用于创建自定义谓词添加到字符串表的名称。

函数原型*f x n*是：

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

值*lpMsg*， *hWndParent*，和*lpRect*参数，将从相应参数的**IOleObject::DoVerb**成员函数。

### <a name="requirements"></a>要求

**标头**afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

使用此宏重写标准谓词的默认行为。

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>参数

*iVerb*  
重写谓词的标准谓词索引。

*f x n*  
框架在调用谓词时调用的函数。

### <a name="remarks"></a>备注

标准谓词索引的形式`OLEIVERB_`后, 跟一个操作。 `OLEIVERB_SHOW`、`OLEIVERB_HIDE` 和 `OLEIVERB_UIACTIVATE` 是标准谓词的一些示例。

请参阅[ON_OLEVERB](#on_oleverb)有关的函数原型用作说明*f x n*参数。


### <a name="requirements"></a>要求

**标头**afxole.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
