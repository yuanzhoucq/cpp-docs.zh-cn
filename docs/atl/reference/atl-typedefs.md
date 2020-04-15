---
title: ATL Typedef
ms.date: 11/04/2016
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319195"
---
# <a name="atl-typedefs"></a>ATL Typedef

活动模板库包括以下类型定义。

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|定义为基于[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)的 typedef。|
|[_ATL_COM_MODULE](#_atl_com_module)|定义为基于[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)的类型定义。|
|[_ATL_MODULE](#_atl_module)|定义为基于[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)的类型定义。|
|[_ATL_WIN_MODULE](#_atl_win_module)|定义为基于[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)的类型定义|
|[ATL_URL_PORT](#atl_url_port)|[CUrl](../../atl/reference/curl-class.md)用于指定端口号的类型。|
|[CCom调度驱动程序](#ccomdispatchdriver)|此类管理 COM 接口指针。|
|[CComGlobalsThread模型](#ccomglobalsthreadmodel)|调用适当的线程模型方法，而不考虑使用的线程模型。|
|[CComObject线程模型](#ccomobjectthreadmodel)|调用适当的线程模型方法，而不考虑使用的线程模型。|
|[包含窗口](#ccontainedwindow)|此类是 的专业化课程`CContainedWindowT`。|
|[CPath](#cpath)|使用[的 CPathT](../../atl/reference/cpatht-class.md)的专门化。 `CString`|
|[查帕](#cpatha)|使用[的 CPathT](../../atl/reference/cpatht-class.md)的专门化。 `CStringA`|
|[CPathW](#cpathw)|使用[的 CPathT](../../atl/reference/cpatht-class.md)的专门化。 `CStringW`|
|[CSimpleValarray](#csimplevalarray)|表示用于存储简单类型的数组。|
|[默认线程特征](#defaultthreadtraits)|默认线程特征类。|
|[LPCURL](#lpcurl)|指向常量[CUrl](../../atl/reference/curl-class.md)对象的指针。|
|[LPURL](#lpurl)|指向[CUrl](../../atl/reference/curl-class.md)对象的指针。|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

定义为基于_ATL_BASE_MODULE70的类型定义。

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>备注

用于每个 ATL 项目。 基于[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。

属于 ATL 7.0 模块类的类派生自_ATL_BASE_MODULE结构。  有关 ATL 模块类的详细信息，请参阅[COM 模块类](../../atl/com-modules-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

定义为基于_ATL_COM_MODULE70的类型定义。

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>备注

使用 COM 功能的 ATL 项目使用。 基于[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

定义为基于_ATL_MODULE70的类型定义。

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>要求

**头：**

### <a name="remarks"></a>备注

基于[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

定义为基于_ATL_WIN_MODULE70的类型定义。

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>备注

使用窗口功能的任何 ATL 项目使用。 基于[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

[CUrl](curl-class.md)用于指定端口号的类型。

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CCom调度驱动程序

此类管理 COM 接口指针。

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThread模型

调用适当的线程模型方法，而不考虑使用的线程模型。

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>备注

根据应用程序使用的线程模型 **，typedef**名称`CComGlobalsThreadModel`引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供用于`typedef`引用关键节类的其他名称。

> [!NOTE]
> `CComGlobalsThreadModel`不引用类[CCom 多线程模型NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComGlobalsThreadModel`可使您从指定特定的线程模型类中释放。 无论使用哪种线程模型，都将调用适当的方法。

除 之外`CComGlobalsThreadModel`，ATL 还提供**类型定义**名称[CComObjectThreadModel](#ccomobjectthreadmodel)。 每个`typedef`类引用的类取决于所使用的线程模型，如下表所示：

|typedef|单线程|公寓线程|免费线程|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

在`CComObjectThreadModel`单个对象类中使用。 在`CComGlobalsThreadModel`程序全局可用的对象中使用，或者当您希望跨多个线程保护模块资源时。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObject线程模型

调用适当的线程模型方法，而不考虑使用的线程模型。

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComObjectThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>备注

根据应用程序使用的线程模型`typedef`，名称`CComObjectThreadModel`引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供用于`typedef`引用关键节类的其他名称。

> [!NOTE]
> `CComObjectThreadModel`不引用类[CCom 多线程模型NoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用`CComObjectThreadModel`可使您从指定特定的线程模型类中释放。 无论使用哪种线程模型，都将调用适当的方法。

除 之外`CComObjectThreadModel`，ATL 还提供**类型定义**名称[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每个**typedef**引用的类取决于所使用的线程模型，如下表所示：

|typedef|单线程|公寓线程|免费线程|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`;M#`CComMultiThreadModel`

在`CComObjectThreadModel`单个对象类中使用。 在`CComGlobalsThreadModel`程序全局可用的对象中，或者当您希望跨多个线程保护模块资源时，请使用该对象。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>包含窗口

此类是 的专业化课程`CContainedWindowT`。

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>要求

**标题：** atlwin.h

### <a name="remarks"></a>备注

`CContainedWindow`是[CContainedWindowT 的](../../atl/reference/ccontainedwindowt-class.md)专业化。 如果要更改基类或特征，请使用`CContainedWindowT`。

## <a name="cpath"></a><a name="cpath"></a>CPath

使用[的 CPathT](../../atl/reference/cpatht-class.md)的专门化。 `CString`

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>要求

**标题：** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>查帕

使用[的 CPathT](../../atl/reference/cpatht-class.md)的专门化。 `CStringA`

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>要求

**标题：** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

使用[的 CPathT](../../atl/reference/cpatht-class.md)的专门化。 `CStringW`

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>要求

**标题：** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValarray

表示用于存储简单类型的数组。

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>备注

`CSimpleValArray`用于创建和管理包含简单数据类型的数组。 这是[一个简单的#defineCSimplearray。](../../atl/reference/csimplearray-class.md)

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

指向常量[CUrl](../../atl/reference/curl-class.md)对象的指针。

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>默认线程特征

默认线程特征类。

### <a name="syntax"></a>语法

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>备注

如果当前项目使用多线程 CRT，则默认线程特征定义为 CRTThreadTraits。 否则，使用 Win32ThreadTraits。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

指向[CUrl](../../atl/reference/curl-class.md)对象的指针。

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="see-also"></a>另请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)<br/>
[函数](../../atl/reference/atl-functions.md)<br/>
[全局变量](../../atl/reference/atl-global-variables.md)<br/>
[类和结构](../../atl/reference/atl-classes.md)<br/>
[宏](../../atl/reference/atl-macros.md)
