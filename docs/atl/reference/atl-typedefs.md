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
ms.openlocfilehash: f3db32e85ea9cba1e946db6259c00c621650e969
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857101"
---
# <a name="atl-typedefs"></a>ATL Typedef

活动模板库包含以下 typedef。

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|定义为基于[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)的 typedef。|
|[_ATL_COM_MODULE](#_atl_com_module)|定义为基于[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)的 typedef。|
|[_ATL_MODULE](#_atl_module)|定义为基于[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)的 typedef。|
|[_ATL_WIN_MODULE](#_atl_win_module)|定义为基于[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)的 typedef|
|[ATL_URL_PORT](#atl_url_port)|用于指定端口号的[卷](../../atl/reference/curl-class.md)的类型。|
|[CComDispatchDriver](#ccomdispatchdriver)|此类管理 COM 接口指针。|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|调用适当的线程模型方法，而不考虑所使用的线程模型。|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|调用适当的线程模型方法，而不考虑所使用的线程模型。|
|[CContainedWindow](#ccontainedwindow)|此类是 `CContainedWindowT`的专用化。|
|[CPath](#cpath)|使用 `CString`的[CPathT](../../atl/reference/cpatht-class.md)的专用化。|
|[CPathA](#cpatha)|使用 `CStringA`的[CPathT](../../atl/reference/cpatht-class.md)的专用化。|
|[CPathW](#cpathw)|使用 `CStringW`的[CPathT](../../atl/reference/cpatht-class.md)的专用化。|
|[CSimpleValArray](#csimplevalarray)|表示用于存储简单类型的数组。|
|[DefaultThreadTraits](#defaultthreadtraits)|默认的线程特征类。|
|[LPCURL](#lpcurl)|指向恒定[曲线](../../atl/reference/curl-class.md)对象的指针。|
|[LPURL](#lpurl)|指向[曲线](../../atl/reference/curl-class.md)对象的指针。|

##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE

定义为基于 _ATL_BASE_MODULE70 的 typedef。

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>备注

用于每个 ATL 项目。 基于[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。

属于 ATL 7.0 模块类的类派生自 _ATL_BASE_MODULE 结构。  有关 ATL 模块类的详细信息，请参阅[COM 模块类](../../atl/com-modules-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcore

##  <a name="_atl_com_module"></a>_ATL_COM_MODULE

定义为基于 _ATL_COM_MODULE70 的 typedef。

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>备注

由使用 COM 功能的 ATL 项目使用。 基于[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="_atl_module"></a>_ATL_MODULE

定义为基于 _ATL_MODULE70 的 typedef。

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>要求

**标头：**

### <a name="remarks"></a>备注

基于[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。

##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE

定义为基于 _ATL_WIN_MODULE70 的 typedef。

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>备注

用于使用窗口化功能的任何 ATL 项目。 基于[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="atl_url_port"></a>ATL_URL_PORT

用于指定端口号的[卷](curl-class.md)的类型。

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>要求

**标头：** atlutil

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver

此类管理 COM 接口指针。

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

调用适当的线程模型方法，而不考虑所使用的线程模型。

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

根据应用程序使用的线程模型， **typedef**名称 `CComGlobalsThreadModel` 引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供附加的 `typedef` 名称来引用临界区类。

> [!NOTE]
> `CComGlobalsThreadModel` 不引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用 `CComGlobalsThreadModel` 使你可以指定特定的线程模型类。 无论使用何种线程模型，都将调用相应的方法。

除了 `CComGlobalsThreadModel`之外，ATL 还提供**typedef**名称[CComObjectThreadModel](#ccomobjectthreadmodel)。 每个 `typedef` 引用的类取决于所使用的线程模型，如下表所示：

|typedef|单线程|单元线程处理|自由线程处理|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

使用单个对象类中的 `CComObjectThreadModel`。 使用在全局可用的对象中的 `CComGlobalsThreadModel`，或在要跨多个线程保护模块资源时使用。

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

调用适当的线程模型方法，而不考虑所使用的线程模型。

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

根据应用程序使用的线程模型，`typedef` 名称 `CComObjectThreadModel` 引用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供附加的 `typedef` 名称来引用临界区类。

> [!NOTE]
> `CComObjectThreadModel` 不引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。

使用 `CComObjectThreadModel` 使你可以指定特定的线程模型类。 无论使用何种线程模型，都将调用相应的方法。

除了 `CComObjectThreadModel`之外，ATL 还提供**typedef**名称[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每个**typedef**引用的类取决于所使用的线程模型，如下表所示：

|typedef|单线程|单元线程处理|自由线程处理|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

使用单个对象类中的 `CComObjectThreadModel`。 使用在全局可用的对象中的 `CComGlobalsThreadModel`，或在要跨多个线程保护模块资源时使用。

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="ccontainedwindow"></a>CContainedWindow

此类是 `CContainedWindowT`的专用化。

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>要求

**标头：** atlwin。h

### <a name="remarks"></a>备注

`CContainedWindow` 是[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)的专用化。 如果要更改基类或特征，请直接使用 `CContainedWindowT`。

##  <a name="cpath"></a>CPath

使用 `CString`的[CPathT](../../atl/reference/cpatht-class.md)的专用化。

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>要求

**标头：** atlpath。h

##  <a name="cpatha"></a>CPathA

使用 `CStringA`的[CPathT](../../atl/reference/cpatht-class.md)的专用化。

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>要求

**标头：** atlpath。h

##  <a name="cpathw"></a>CPathW

使用 `CStringW`的[CPathT](../../atl/reference/cpatht-class.md)的专用化。

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>要求

**标头：** atlpath。h

##  <a name="csimplevalarray"></a>CSimpleValArray

表示用于存储简单类型的数组。

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>备注

提供 `CSimpleValArray` 用于创建和管理包含简单数据类型的数组。 这是[CSimpleArray](../../atl/reference/csimplearray-class.md)的简单 #define。

## <a name="requirements"></a>要求

**标头：** atlsimpcoll

##  <a name="lpcurl"></a>LPCURL

指向恒定[曲线](../../atl/reference/curl-class.md)对象的指针。

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>要求

**标头：** atlutil

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits

默认的线程特征类。

### <a name="syntax"></a>语法

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>备注

如果当前项目使用多线程 CRT，则将 DefaultThreadTraits 定义为 CRTThreadTraits。 否则，将使用 Win32ThreadTraits。

## <a name="requirements"></a>要求

**标头：** atlbase。h

##  <a name="lpurl"></a>LPURL

指向[曲线](../../atl/reference/curl-class.md)对象的指针。

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>要求

**标头：** atlutil

## <a name="see-also"></a>另请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)<br/>
[函数](../../atl/reference/atl-functions.md)<br/>
[全局变量](../../atl/reference/atl-global-variables.md)<br/>
[类和结构](../../atl/reference/atl-classes.md)<br/>
[宏](../../atl/reference/atl-macros.md)
