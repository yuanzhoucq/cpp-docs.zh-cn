---
title: "ATL Typedef |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d721cefd20ae5eb208c74d973069fb9365273d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-typedefs"></a>ATL Typedef
活动模板库包括以下 typedef。  
  
|||  
|-|-|  
|[_ATL_BASE_MODULE](#_atl_base_module)|定义为基于的 typedef [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。|  
|[_ATL_COM_MODULE](#_atl_com_module)|定义为基于的 typedef [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。|  
|[_ATL_MODULE](#_atl_module)|定义为基于的 typedef [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。|  
|[_ATL_WIN_MODULE](#_atl_win_module)|定义为基于的 typedef [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|  
|[ATL_URL_PORT](#atl_url_port)|使用的类型[CUrl](../../atl/reference/curl-class.md)用于指定端口号。|  
|[CComDispatchDriver](#ccomdispatchdriver)|此类管理 COM 接口指针。|  
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|调用适当的线程模型的方法，而不考虑所使用的线程模型。|  
|[CComObjectThreadModel](#ccomobjectthreadmodel)|调用适当的线程模型的方法，而不考虑所使用的线程模型。|  
|[CContainedWindow](#ccontainedwindow)|此类是的专用化**CContainedWindowT。**|  
|[CPath](#cpath)|专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CString`。|  
|[CPathA](#cpatha)|专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringA`。|  
|[CPathW](#cpathw)|专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringW`。|  
|[CSimpleValArray](#csimplevalarray)|表示用于存储简单类型的数组。|  
|[DefaultThreadTraits](#defaultthreadtraits)|默认线程的特征类。|  
|[LPCURL](#lpcurl)|指向常量[CUrl](../../atl/reference/curl-class.md)对象。|  
|[LPURL](#lpurl)|指向的指针[CUrl](../../atl/reference/curl-class.md)对象。|  
  
##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE  
 定义为基于 _ATL_BASE_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;   
```  
  
### <a name="remarks"></a>备注  
 在每个 ATL 项目中使用。 基于[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。  
  
 属于的 ATL 7.0 Module 类的类派生自 _ATL_BASE_MODULE 结构。  有关 ATL Module 类的详细信息，请参阅[COM 模块类](../../atl/com-modules-classes.md)。  

## <a name="requirements"></a>惠?
**标头：** atlcore.h

##  <a name="_atl_com_module"></a>_ATL_COM_MODULE  
 定义为基于 _ATL_COM_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;   
```  
  
### <a name="remarks"></a>备注  
 使用 ATL 项目使用 COM 功能。 基于[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。  

## <a name="requirements"></a>惠?
**标头：** atlbase.h
  
##  <a name="_atl_module"></a>_ATL_MODULE  
 定义为基于 _ATL_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_MODULE70 _ATL_MODULE;   
```  
## <a name="requirements"></a>惠?
**标头：** 
  
### <a name="remarks"></a>备注  
 基于[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。  
  
##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE  
 定义为基于 _ATL_WIN_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE; 
 
```  
  
### <a name="remarks"></a>备注  
 使用任何 ATL 项目使用窗口化功能。 基于[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。  

## <a name="requirements"></a>惠?
**标头：** atlbase.h 
  
##  <a name="atl_url_port"></a>ATL_URL_PORT 
  使用的类型[CUrl](curl-class.md)用于指定端口号。
```  
typedef WORD ATL_URL_PORT;
```  

## <a name="requirements"></a>惠?
**标头：** atlutil.h

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver  
 此类管理 COM 接口指针。  
  
```   
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;   
```  
## <a name="requirements"></a>惠?
**标头：** atlbase.h
  
##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel  
 调用适当的线程模型的方法，而不考虑所使用的线程模型。  
  
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
 具体取决于应用程序使用的线程模型`typedef`名称`CComGlobalsThreadModel`引用或者[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供其他`typedef`名称来引用临界区类。  
  
> [!NOTE]
> `CComGlobalsThreadModel`不引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  
  
 使用`CComGlobalsThreadModel`使你指定特定的线程处理模型类。 无论正在使用的线程处理模型，将调用适当的方法。  
  
 除了`CComGlobalsThreadModel`，ATL 提供`typedef`名称[CComObjectThreadModel](#ccomobjectthreadmodel)。 每个所引用类`typedef`依赖于使用的线程处理模型下, 表中所示：  
  
|typedef|单个线程处理|单元线程处理|自由线程处理|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 使用`CComObjectThreadModel`中单个对象类。 使用`CComGlobalsThreadModel`全局可用于您的程序，或者在你想要保护跨多个线程的模块资源的对象中。  

## <a name="requirements"></a>惠?
**标头：** atlbase.h
  
##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel  
 调用适当的线程模型的方法，而不考虑所使用的线程模型。  
  
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
 具体取决于应用程序使用的线程模型`typedef`名称`CComObjectThreadModel`引用或者[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供其他`typedef`名称来引用临界区类。  
  
> [!NOTE]
> `CComObjectThreadModel`不引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  
  
 使用`CComObjectThreadModel`使你指定特定的线程处理模型类。 无论正在使用的线程处理模型，将调用适当的方法。  
  
 除了`CComObjectThreadModel`，ATL 提供`typedef`名称[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 每个所引用类`typedef`依赖于使用的线程处理模型下, 表中所示：  
  
|typedef|单个线程处理|单元线程处理|自由线程处理|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 使用`CComObjectThreadModel`中单个对象类。 使用`CComGlobalsThreadModel`对象中是全局可用到你的程序，或当你想要保护跨多个线程的模块资源。  

## <a name="requirements"></a>惠?
**标头：** atlbase.h
  
##  <a name="ccontainedwindow"></a>CContainedWindow  
 此类是的专用化**CContainedWindowT。**  
  
```   
typedef CContainedWindowT<CWindow> CContainedWindow;   
```  

## <a name="requirements"></a>惠?
**标头：** atlwin.h
  
### <a name="remarks"></a>备注  
 `CContainedWindow`是的专用化[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)。 如果你想要更改的基类或特征，使用`CContainedWindowT`直接。  
  
##  <a name="cpath"></a>CPath  
 专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CString`。  
  
```   
typedef CPathT<CString> CPath;   
```  

## <a name="requirements"></a>惠?
**标头：** atlpath.h
  
##  <a name="cpatha"></a>CPathA  
 专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringA`。  
  
```   
typedef CPathT<CStringA> CPathA;   
```

## <a name="requirements"></a>惠?
**标头：** atlpath.h  
  
##  <a name="cpathw"></a>CPathW  
 专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringW`。  
  
```   
typedef ATL::CPathT<CStringW> CPathW;   
```  
## <a name="requirements"></a>惠?
**标头：** atlpath.h
  
##  <a name="csimplevalarray"></a>CSimpleValArray  
 表示用于存储简单类型的数组。  
  
```   
#define CSimpleValArray CSimpleArray   
```  

  
### <a name="remarks"></a>备注  
 `CSimpleValArray`提供用于创建和管理包含简单数据类型的数组。 它是一个简单 #define 的[CSimpleArray](../../atl/reference/csimplearray-class.md)。  


## <a name="requirements"></a>惠?
**标头：** atlsimpcoll.h
  
##  <a name="lpcurl"></a>LPCURL  
 指向常量[CUrl](../../atl/reference/curl-class.md)对象。  
  
```   
typedef const CUrl* LPCURL;   
```  

## <a name="requirements"></a>惠?
**标头：** atlutil.h

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits
默认线程的特征类。

### <a name="syntax"></a>语法
```  
      #if defined(_MT)  
   typedef CRTThreadTraits DefaultThreadTraits;  
#else  
   typedef Win32ThreadTraits DefaultThreadTraits;  
#endif  
```

## <a name="remarks"></a>备注
如果当前的项目使用多线程的 CRT，DefaultThreadTraits 被指 CRTThreadTraits。 否则，使用 Win32ThreadTraits。


## <a name="requirements"></a>惠?
**标头：** atlbase.h
  
##  <a name="lpurl"></a>LPURL  
 指向的指针[CUrl](../../atl/reference/curl-class.md)对象。  
  
```   
typedef CUrl* LPURL;   
```  

## <a name="requirements"></a>惠?
**标头：** atlutil.h


## <a name="see-also"></a>请参阅  
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)   
 [函数](../../atl/reference/atl-functions.md)   
 [全局变量](../../atl/reference/atl-global-variables.md)   
 [结构](../../atl/reference/atl-structures.md)   
 [宏](../../atl/reference/atl-macros.md)   
 [类](../../atl/reference/atl-classes.md)