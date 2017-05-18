---
title: "ATL Typedef |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 347e7bf7cd9173fb2815f44fc052ec23ab4055a6
ms.openlocfilehash: aa57212b602538e4e8d2854c6075562e72472796
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="atl-typedefs"></a>ATL Typedef
活动模板库包括以下的 typedef。  
  
|||  
|-|-|  
|[_ATL_BASE_MODULE](#_atl_base_module)|定义为基于的 typedef [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。|  
|[_ATL_COM_MODULE](#_atl_com_module)|定义为基于的 typedef [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。|  
|[_ATL_MODULE](#_atl_module)|定义为基于的 typedef [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。|  
|[_ATL_WIN_MODULE](#_atl_win_module)|定义为基于的 typedef [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|  
|[ATL_URL_PORT](#atl_url_port)|所使用的类型[CUrl](../../atl/reference/curl-class.md)用于指定端口号。|  
|[CComDispatchDriver](#ccomdispatchdriver)|此类管理 COM 接口指针。|  
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|调用适当的线程模型的方法，而不考虑要使用的线程模型。|  
|[CComObjectThreadModel](#ccomobjectthreadmodel)|调用适当的线程模型的方法，而不考虑要使用的线程模型。|  
|[CContainedWindow](#ccontainedwindow)|此类是专用化**CContainedWindowT。**|  
|[CPath](#cpath)|专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CString`。|  
|[CPathA](#cpatha)|专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringA`。|  
|[CPathW](#cpathw)|专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringW`。|  
|[CSimpleValArray](#csimplevalarray)|表示用于存储的简单类型的数组。|  
|[DefaultThreadTraits](#defaultthreadtraits)|默认值的线程特征类。|  
|[LPCURL](#lpcurl)|指向常量指针[CUrl](../../atl/reference/curl-class.md)对象。|  
|[LPURL](#lpurl)|一个指向[CUrl](../../atl/reference/curl-class.md)对象。|  
  
##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE  
 定义为基于 _ATL_BASE_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;   
```  
  
### <a name="remarks"></a>备注  
 使用 ATL 中的每个项目。 基于[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)。  
  
 属于的 ATL 7.0 Module 类的类派生自 _ATL_BASE_MODULE 结构。  ATL Module 类的详细信息，请参阅[COM 模块类](../../atl/com-modules-classes.md)。  
  
##  <a name="_atl_com_module"></a>_ATL_COM_MODULE  
 定义为基于 _ATL_COM_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;   
```  
  
### <a name="remarks"></a>备注  
 使用 ATL 项目使用 COM 功能。 基于[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)。  
  
##  <a name="_atl_module"></a>_ATL_MODULE  
 定义为基于 _ATL_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_MODULE70 _ATL_MODULE;   
```  
  
### <a name="remarks"></a>备注  
 基于[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)。  
  
##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE  
 定义为基于 _ATL_WIN_MODULE70 的 typedef。  
  
```   
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE; 
 
```  
  
### <a name="remarks"></a>备注  
 使用由任何 ATL 项目使用窗口功能。 基于[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)。  
  
##  <a name="atl_url_port"></a>ATL_URL_PORT 
  所使用的类型[CUrl](curl-class.md)用于指定端口号。
```  
typedef WORD ATL_URL_PORT;
```  

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver  
 此类管理 COM 接口指针。  
  
```   
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;   
```  
  
##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel  
 调用适当的线程模型的方法，而不考虑要使用的线程模型。  
  
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
 具体取决于应用程序使用的线程模型`typedef`名称`CComGlobalsThreadModel`引用或者[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供了其他`typedef`名称来引用一个关键部分类。  
  
> [!NOTE]
> `CComGlobalsThreadModel`未引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  
  
 使用`CComGlobalsThreadModel`让你指定特定的线程模型类。 无论所使用的线程模型，将调用适当的方法。  
  
 除了`CComGlobalsThreadModel`，ATL 还提供`typedef`名称[CComObjectThreadModel](#ccomobjectthreadmodel)。 由每个引用的类`typedef`，所使用的线程模型取决于下表中所示︰  
  
|typedef|单线程|单元线程处理|自由线程处理|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 使用`CComObjectThreadModel`中单个对象类。 使用`CComGlobalsThreadModel`中对象的全局可供您的程序，或如果想要保护跨多个线程的模块资源。  
  
##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel  
 调用适当的线程模型的方法，而不考虑要使用的线程模型。  
  
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
 具体取决于应用程序使用的线程模型`typedef`名称`CComObjectThreadModel`引用或者[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。 这些类提供了其他`typedef`名称来引用一个关键部分类。  
  
> [!NOTE]
> `CComObjectThreadModel`未引用类[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  
  
 使用`CComObjectThreadModel`让你指定特定的线程模型类。 无论所使用的线程模型，将调用适当的方法。  
  
 除了`CComObjectThreadModel`，ATL 还提供`typedef`名称[CComGlobalsThreadModel](#ccomglobalsthreadmodel)。 由每个引用的类`typedef`，所使用的线程模型取决于下表中所示︰  
  
|typedef|单线程|单元线程处理|自由线程处理|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`;M =`CComMultiThreadModel`  
  
 使用`CComObjectThreadModel`中单个对象类。 使用`CComGlobalsThreadModel`对象，则为中全局可用到您的程序，或者当您想要保护跨多个线程的模块资源。  
  
##  <a name="ccontainedwindow"></a>CContainedWindow  
 此类是专用化**CContainedWindowT。**  
  
```   
typedef CContainedWindowT<CWindow> CContainedWindow;   
```  
  
### <a name="remarks"></a>备注  
 `CContainedWindow`专用化的[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)。 如果你想要更改的基类或特征，使用`CContainedWindowT`直接。  
  
##  <a name="cpath"></a>CPath  
 专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CString`。  
  
```   
typedef CPathT<CString> CPath;   
```  
  
##  <a name="cpatha"></a>CPathA  
 专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringA`。  
  
```   
typedef CPathT<CStringA> CPathA;   
```  
  
##  <a name="cpathw"></a>CPathW  
 专用化[CPathT](../../atl/reference/cpatht-class.md)使用`CStringW`。  
  
```   
typedef ATL::CPathT<CStringW> CPathW;   
```  
  
##  <a name="csimplevalarray"></a>CSimpleValArray  
 表示用于存储的简单类型的数组。  
  
```   
#define CSimpleValArray CSimpleArray   
```  
  
### <a name="remarks"></a>备注  
 `CSimpleValArray`提供用于创建和管理包含简单的数据类型的数组。 它是一个简单的 #define 的[CSimpleArray](../../atl/reference/csimplearray-class.md)。  
  
##  <a name="lpcurl"></a>LPCURL  
 指向常量指针[CUrl](../../atl/reference/curl-class.md)对象。  
  
```   
typedef const CUrl* LPCURL;   
```  

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits
默认值的线程特征类。

### <a name="syntax"></a>语法
```  
      #if defined(_MT)  
   typedef CRTThreadTraits DefaultThreadTraits;  
#else  
   typedef Win32ThreadTraits DefaultThreadTraits;  
#endif  
```

## <a name="remarks"></a>备注
如果当前项目使用多线程的 CRT，DefaultThreadTraits 被指 CRTThreadTraits。 否则，使用 Win32ThreadTraits。
  
##  <a name="lpurl"></a>LPURL  
 一个指向[CUrl](../../atl/reference/curl-class.md)对象。  
  
```   
typedef CUrl* LPURL;   
```  
  
## <a name="see-also"></a>另请参阅  
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)   
 [函数](../../atl/reference/atl-functions.md)   
 [全局变量](../../atl/reference/atl-global-variables.md)   
 [结构](../../atl/reference/atl-structures.md)   
 [宏](../../atl/reference/atl-macros.md)   
 [类](../../atl/reference/atl-classes.md)
