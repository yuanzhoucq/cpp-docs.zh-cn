---
title: ATL 类和结构 |Microsoft Docs
ms.custom: ''
ms.date: 05/03/2018
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71025785fbc9eab2b962e0f9e48ba9170edf1de1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204185"
---
# <a name="atl-classes-and-structs"></a>ATL 类和结构
活动模板库 (ATL) 包括以下类和结构。 若要按类别查找特定的类，请参阅[ATL 类概述](../../atl/atl-class-overview.md)。  
  
|类 / 结构|描述|头文件|  
|-----------|-----------------|-----------------|  
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|包含用于呈现到各种目标，如打印机、 图元文件或 ActiveX 控件的信息。|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|包含在 atl。 窗口化代码中的类实例数据|atlbase.h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|使用的任何项目都使用 ATL|atlbase.h|  
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|由 COM 相关代码在 atl。| atlbase.h|  
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|包含用于描述调度接口方法或属性的类型信息。|atlcom.h|  
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|包含使用 ATL 的每个模块的数据。|atlbase.h|  
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|使用开窗中的代码 atl。|atlbase.h|  
|[CA2AEX](../../atl/reference/ca2aex-class.md)|字符串转换宏 CA2TEX 和 CT2AEX 和 typedef CA2A 使用此类。|atlconv.h|  
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|字符串转换宏 CA2CTEX 和 CT2CAEX 和 typedef CA2CA 使用此类。|atlconv.h|  
|[CA2WEX](../../atl/reference/ca2wex-class.md)|字符串转换宏 CA2TEX、 CA2CTEX、 CT2WEX，和 CT2CWEX 和 typedef CA2W 使用此类。|atlconv.h|  
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|此类是访问令牌的包装器。|atlsecurity.h|  
|[CAcl](../../atl/reference/cacl-class.md)|此类是 ACL （访问控制列表） 结构的包装器。|atlsecurity.h|  
|[CAdapt](../../atl/reference/cadapt-class.md)|此模板用于包装一些类，这些类将 address-of 运算符重新定义为返回对象地址之外的内容。|atlcomcli.h|  
|[CAtlArray](../../atl/reference/catlarray-class.md)|此类实现一个数组对象。|atlcoll.h|  
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|此类实现为在线程池的单元模型 COM 服务器。|atlbase.h|  
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|此类提供用于实现为在线程池的单元模型 COM 服务器的方法。|atlbase.h|  
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|每个 ATL 项目中实例化此类。|atlcore.h|  
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|此类实现的 COM 服务器模块。|atlbase.h|  
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|此类为调试接口提供支持。|atlbase.h|  
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|此类表示对 dll 的模块。|atlbase.h|  
|[CAtlException](../../atl/reference/catlexception-class.md)|此类定义 ATL 异常。|atlexcept.h|  
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|此类表示应用程序的模块。|atlbase.h|  
|[CAtlFile](../../atl/reference/catlfile-class.md)|此类提供了 Windows 的薄包装器文件处理 API。|atlfile.h|  
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|此类表示一个内存映射文件，将强制转换运算符添加到的方法[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。|atlfile.h|  
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|此类表示一个内存映射文件。|atlfile.h|  
|[CAtlList](../../atl/reference/catllist-class.md)|此类提供用于创建和管理列表对象的方法。|atlcoll.h|  
|[CAtlMap](../../atl/reference/catlmap-class.md)|此类提供用于创建和管理 map 对象的方法。|atlcoll.h|  
|[CAtlModule](../../atl/reference/catlmodule-class.md)|此类提供使用多个 ATL module 类的方法。|atlbase.h|  
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|此类实现的 ATL 模块。|atlbase.h|  
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|此类是 ATL 实现位于 shell 提供用于丰富预览的宿主窗口的窗口。|atlpreviewctrlimpl.h|  
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|此类实现一种服务。|atlbase.h|  
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|此类提供用于创建和使用的临时文件的方法。|atlfile.h|  
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|此类提供对内核事务管理器 (KTM) 函数的包装器。|atltransactionmanager.h|  
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|此类的 ATL 窗口化组件提供支持。|atlbase.h|  
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|此类表示一个智能指针对象。|atlbase.h|  
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|构造的智能指针的数组时，此类提供了有用的方法。|atlbase.h|  
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|在创建集合的智能指针时，此类提供方法、 静态函数和有用的 typedef。|atlcoll.h|  
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|构造的智能指针的列表时，此类提供了有用的方法。|atlcoll.h|  
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|此类表示智能指针对象在使用矢量 new 和 delete 运算符。|atlbase.h|  
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|此类提供方法、 静态函数和类型定义时创建的使用向量的新的智能指针的集合和 delete 运算符很有用。|atlcoll.h|  
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|此类实现一个对话框 （模式或无模式） 承载 ActiveX 控件。|atlwin.h|  
|[CAxWindow](../../atl/reference/caxwindow-class.md)|此类提供用于操作承载 ActiveX 控件的窗口的方法。|atlwin.h|  
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|此类提供用于操作的窗口，承载 ActiveX 控件并具有的用于托管授权的 ActiveX 控件支持的方法。|atlwin.h|  
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|此类实现 `IBindStatusCallback` 接口。|atlctl.h|  
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|此类实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)聚合对象。|atlcom.h|  
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|此类提供用于管理内存使用 COM 内存例程的方法。|atlbase.h|  
|[CComApartment](../../atl/reference/ccomapartment-class.md)|此类用于管理线程放入池中 EXE 模块中的某个单元提供支持。|atlbase.h|  
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|此类提供方法用于获取并释放关键节对象的所有权。|atlcore.h|  
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|ATL 7.0 起`CComAutoThreadModule`已过时： 请参阅[ATL 模块](../../atl/atl-module-classes.md)的更多详细信息。|atlbase.h|  
|[CComBSTR](../../atl/reference/ccombstr-class.md)|此类是 Bstr 的包装器。|atlbase.h|  
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|此类实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)分离式接口。|atlcom.h|  
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|此类实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。|atlcom.h|  
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|此类实现[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)接口。|atlcom.h|  
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|此类实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建的对象。|atlcom.h|  
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|此类派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造一个单一对象。|atlcom.h|  
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|此类提供用于创建类的实例并获取其属性的方法。|atlcom.h|  
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|此类提供用于实现复合控件所需的方法。|atlctl.h|  
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|此类实现[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)通过将委派给所有者对象`IUnknown`。|atlcom.h|  
|[CComControl](../../atl/reference/ccomcontrol-class.md)|此类提供用于创建和管理 ATL 控件的方法。|atlctl.h|  
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|此类提供用于创建和管理 ATL 控件的方法。|atlctl.h|  
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|此类提供方法用于获取并释放关键节对象的所有权。|atlcore.h|  
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|此类提供用于锁定和解锁关键部分对象的方法。|atlbase.h|  
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|此类具有用于创建和管理 CURRENCY 对象的方法和运算符。|atlcur.h|  
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|此类存储数组的`IUnknown`指针。|atlcom.h|  
|[CComEnum](../../atl/reference/ccomenum-class.md)|此类定义基于数组的 COM 枚举器对象。|atlcom.h|  
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|此类提供要枚举的项数组中的存储位置的 COM 枚举器接口的实现。|atlcom.h|  
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|此类定义一个基于 c + + 标准库集合的 COM 枚举器对象。|atlcom.h|  
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|此类提供了将相同的方法作为[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ，但不提供关键部分。|atlcore.h|  
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|此类提供用于处理接口指针的方法和全局接口表 (GIT)。|atlbase.h|  
|[CComHeap](../../atl/reference/ccomheap-class.md)|此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 COM 内存分配函数。|ATLComMem.h|  
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|用于管理堆指针的智能指针类。|atlbase.h|  
|[CComModule](../../atl/reference/ccommodule-class.md)|ATL 7.0 起`CComModule`已过时： 请参阅[ATL 模块](../../atl/atl-module-classes.md)的更多详细信息。|atlbase.h|  
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|此类提供线程安全方法递增和递减的变量的值。|atlbase.h|  
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|此类提供线程安全方法递增和递减的值的变量，而无需临界区锁定或解锁功能。|atlbase.h|  
|[CComObject](../../atl/reference/ccomobject-class.md)|此类实现`IUnknown`非聚合对象。|atlcom.h|  
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|此类管理模块包含的引用计数在`Base`对象。|atlcom.h|  
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|此类实现`IUnknown`的非聚合的对象，但不会递增模块锁计数的构造函数中。|atlcom.h|  
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|Typedef [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)针对线程处理模型的服务器的默认模板化。|atlcom.h|  
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|此类提供方法以处理非聚合和聚合对象的对象引用计数管理。|atlcom.h|  
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|此类创建临时的 COM 对象，并为其提供的主干实现`IUnknown`。|atlcom.h|  
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|此类实现`IUnknown`聚合或非聚合对象。|atlcom.h|  
|[CComPtr](../../atl/reference/ccomptr-class.md)|用于管理 COM 接口指针的智能指针类。|atlcomcli.h|  
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|此类为使用基于 COM 的内存例程的智能指针类提供了基础。|atlcomcli.h|  
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|用于管理 COM 接口指针的智能指针类。|atlcomcli.h|  
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|创建的 COM 接口指针的集合时，此类提供了方法、 静态函数和有用的 typedef。|atlcoll.h|  
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|此类是包装`SAFEARRAY Data Type`结构。|atlsafe.h|  
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|此类是包装`SAFEARRAYBOUND`结构。|atlsafe.h|  
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|此类管理线程选择该类[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。|atlbase.h|  
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|此类提供用于方法递增和递减变量的值。|atlbase.h|  
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|此类实现分离式接口。|atlcom.h|  
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|此类存储`IUnknown`指针，它旨在用作参数[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类。|atlcom.h|  
|[CComVariant](../../atl/reference/ccomvariant-class.md)|此类包装提供存储的数据类型，该值指示成员的变体类型。|atlcomcli.h|  
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|此类实现包含在另一个对象内的窗口。|atlwin.h|  
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|此类提供用于管理内存使用的内存 CRT 例程的方法。|atlcore.h|  
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 CRT 堆函数。|atlmem.h|  
|[CDacl](../../atl/reference/cdacl-class.md)|此类是 DACL （自由访问控制列表） 结构的包装器。|atlsecurity.h|  
|[CDebugReportHook 类](../../atl/reference/cdebugreporthook-class.md)|使用此类将调试报告发送到命名管道。|atlutil.h|  
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|此类提供两个静态函数转换为大写和小写字母之间的字符。|atlcoll.h|  
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|此类提供了默认元素比较函数。|atlcoll.h|  
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|此类集合类提供默认方法和函数。|atlcoll.h|  
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|此类提供一个静态函数用于计算哈希值。|atlcoll.h|  
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|此类提供用于创建模式对话框或无模式对话框的方法。|atlwin.h|  
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|此类提供了支持消息映射的动态链接的方法。|atlwin.h|  
|[CElementTraits](../../atl/reference/celementtraits-class.md)|此类是集合类用于为移动、 复制、 比较和哈希操作提供方法和函数。|atlcoll.h|  
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|此类提供默认复制并移动集合类的方法。|atlcoll.h|  
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|此类提供用于通知与控件属性更改有关容器的接收器的方法。|atlctl.h|  
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 全局堆函数。|atlmem.h|  
|[CHandle](../../atl/reference/chandle-class.md)|此类提供用于创建和使用句柄对象的方法。|atlbase.h|  
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|用于管理堆指针的智能指针类。|atlcore.h|  
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|此类窗体智能堆指针的多个类的基础。|atlcore.h|  
|[CHeapPtrElementTraits 类](../../atl/reference/cheapptrelementtraits-class.md)|在创建集合的堆指针时，此类提供方法、 静态函数和有用的 typedef。|atlcoll.h|  
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|构造的堆指针的列表时，此类提供了有用的方法。|atlcoll.h|  
|[中的 CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供了增强的位图支持，包括加载和保存 JPEG、 GIF、 BMP、 和可移植网络图形 (PNG) 格式图像的能力。|atlimage.h|  
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|构造的 COM 接口指针的数组时，此类提供了有用的方法。|atlcoll.h|  
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|构造的 COM 接口指针的列表时，此类提供了有用的方法。|atlcoll.h|  
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 本地堆函数。|atlmem.h|  
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|此类允许对象的消息映射来访问另一个对象。|atlwin.h|  
|[CNonStatelessWorker 类](../../atl/reference/cnonstatelessworker-class.md)|从线程池中接收请求并将它们传递到创建和销毁的工作对象上每个请求。|atlutil.h|  
|[CNoWorkerThread 类](../../atl/reference/cnoworkerthread-class.md)|使用此类的自变量作为`MonitorClass`模板参数缓存类，如果你想要禁用动态缓存维护。|atlutil.h|  
|[CPathT 类](../../atl/reference/cpatht-class.md)|此类表示的路径。|atlpath.h|  
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|此类提供默认方法和集合类的函数组成的基元数据类型。|atlcoll.h|  
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|此类表示私有对象安全描述符对象。|atlsecurity.h|  
|[CRBMap](../../atl/reference/crbmap-class.md)|此类表示映射结构，使用红黑二进制树。|atlcoll.h|  
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|此类表示允许每个密钥要与多个值，使用红黑二进制树关联的映射结构。|atlcoll.h|  
|[CRBTree](../../atl/reference/crbtree-class.md)|此类提供用于创建和使用红黑树的方法。|atlcoll.h|  
|[CRegKey](../../atl/reference/cregkey-class.md)|此类提供用于操作在系统注册表中的条目的方法。|atlbase.h|  
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|此类提供 CRT 线程的创建函数。 如果该线程将使用的 CRT 函数，请使用此类。|atlbase.h|  
|[CSacl](../../atl/reference/csacl-class.md)|此类是一个 SACL （系统访问控制列表） 结构的包装器。|atlsecurity.h|  
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|此类是瘦包装程序`SECURITY_ATTRIBUTES`结构。|atlsecurity.h|  
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|此类是包装`SECURITY_DESCRIPTOR`结构。|atlsecurity.h|  
|[CSid](../../atl/reference/csid-class.md)|此类是包装`SID`（安全标识符） 结构。|atlsecurity.h|  
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|此类提供用于管理简单数组的方法。|atlsimpcoll.h|  
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|此类是一个帮助程序对于[CSimpleArray](../../atl/reference/csimplearray-class.md)类。|atlsimpcoll.h|  
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|此类是一个帮助程序对于[CSimpleArray](../../atl/reference/csimplearray-class.md)类。|atlsimpcoll.h|  
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|此类实现基本的模式对话框。|atlwin.h|  
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|此类简单映射数组提供支持。|atlsimpcoll.h|  
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|此类是一个帮助程序对于[CSimpleMap](../../atl/reference/csimplemap-class.md)类。|atlsimpcoll.h|  
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|此类是一个帮助程序对于[CSimpleMap](../../atl/reference/csimplemap-class.md)类。|atlsimpcoll.h|  
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|此类提供用于实现管理单元中节点对象的方法。|atlsnap.h|  
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|此类提供用于实现一个管理单元中属性的 page 对象的方法。|atlsnap.h|  
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|此类提供支持的常用属性值的方法。|atlctl.h|  
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|此类提供了使用的存储的集合类的静态函数`CString`对象。|cstringt.h|  
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|此类提供与集合类对象中存储的字符串相关的静态函数。 它是类似于[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但执行不区分大小写的比较。|atlcoll.h|  
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|此类提供与集合类对象中存储的字符串相关的静态函数。 以引用方式处理字符串对象。|atlcoll.h|  
|[CThreadPool 类](../../atl/reference/cthreadpool-class.md)|此类提供处理的工作项队列的工作线程的池。|atlutil.h|  
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|此类是包装`TOKEN_GROUPS`结构。|atlsecurity.h|  
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|此类是包装`TOKEN_PRIVILEGES`结构。|atlsecurity.h|  
|[CUrl 类](../../atl/reference/curl-class.md)|此类表示的 URL。 它允许您分析现有的 URL 是否处理每个元素独立于其他 URL 的字符串或生成一个从零开始的字符串。|atlutil.h|  
|[CW2AEX](../../atl/reference/cw2aex-class.md)|字符串转换宏 CT2AEX、 CW2TEX、 CW2CTEX，和 CT2CAEX 和 typedef CW2A 使用此类。|atlconv.h|  
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|字符串转换宏 CW2CTEX 和 CT2CWEX 和 typedef CW2CW 使用此类。|atlconv.h|  
|[CW2WEX](../../atl/reference/cw2wex-class.md)|字符串转换宏 CW2TEX 和 CT2WEX 和 typedef CW2W 使用此类。|atlconv.h|  
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|此类实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 堆分配函数。|atlmem.h|  
|[CWindow](../../atl/reference/cwindow-class.md)|此类提供用于处理窗口的方法。|atlwin.h|  
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|此类提供用于创建或子类化窗口的方法。|atlwin.h|  
|[CWinTraits](../../atl/reference/cwintraits-class.md)|此类提供方法来标准化创建窗口对象时所用的样式。|atlwin.h|  
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|此类提供方法来标准化创建窗口对象时所用的样式。|atlwin.h|  
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|此类提供了用于注册窗口类信息的方法。|atlwin.h|  
|[CWorkerThread 类](../../atl/reference/cworkerthread-class.md)|此类创建工作线程或使用现有工作区，等待上一个或多个内核对象句柄，并发出一个句柄的信号时执行指定的客户端函数。|atlutil.h|  
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|此类表示的接口`CreateInstance`方法。|atlbase.h|  
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|此类表示为内存管理器的接口。|atlmem.h|  
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|此接口提供了用于指定承载的控件或容器的特征的方法。|atlbase.h ATLIFace.h|  
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|此接口实现托管控件的补充环境的属性。|atlbase.h ATLIFace.h|  
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|此接口提供用于操作控件和其宿主对象的方法。|atlbase.h ATLIFace.h|  
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|此接口提供用于操作授权的控件和其宿主对象的方法。|atlbase.h ATLIFace.h|  
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|此类提供了使用集合类的方法。|atlcom.h|  
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|此类实现连接点容器来管理一系列[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象。|atlcom.h|  
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|此类实现连接点。|atlcom.h|  
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|此类提供用于支持统一数据传输和管理连接的方法。|atlctl.h|  
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|此类提供的默认实现`IDispatch`双重接口的一部分。|atlcom.h|  
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|此类提供的实现`IDispatch`方法。|atlcom.h|  
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|此类提供的实现`IDispatch`方法，而不从类型库中获取类型信息。|atlcom.h|  
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Microsoft HTML 分析和呈现引擎的接口。|atlbase.h ATLIFace.h|  
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|此类定义基于 c + + 标准库集合的枚举器接口。|atlcom.h|  
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|此类提供的默认实现`IObjectSafety`接口，以允许客户端来检索和设置对象的安全级别。|atlctl.h|  
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|此类提供允许其站点进行通信的对象的方法。|atlcom.h|  
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|此类提供的默认实现`IOleControl`接口并实现`IUnknown`。|atlctl.h|  
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|此类提供方法，可帮助在就地控件与其容器之间的通信。|atlctl.h|  
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|此类实现`IUnknown`并提供启用无窗口控件接收窗口消息并将参与拖放操作的方法。|atlctl.h|  
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|此类实现`IUnknown`是通过该容器与控件进行通信的主体接口。|atlctl.h|  
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|此类实现`IUnknown`和允许客户端访问对象的属性页中的信息。|atlctl.h|  
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|此类实现`IUnknown`和允许对象将其属性保存到客户端提供的属性包。|atlcom.h|  
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|此类实现[IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage)接口。|atlcom.h|  
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|此类实现`IUnknown`，并提供的默认实现[IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit)接口。|atlcom.h|  
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|此类实现`IUnknown`并[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive)接口方法。|atlctl.h|  
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|此类公开[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)作为可连接对象上的传出接口的接口。|atlctl.h|  
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|此类实现`IUnknown`和继承的默认实现[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)。|atlctl.h|  
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|此类实现`IUnknown`，并提供的默认实现[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)接口。|atlctl.h|  
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|此类提供的默认实现[IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo)并[IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2)方法。|atlcom.h|  
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|此类将合并到一个调用容器的控件初始化。|atlctl.h|  
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|此类实现`IUnknown`，并提供的默认实现[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject)接口。|atlctl.h|  
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|此类提供的默认实现`IServiceProvider`接口。|atlcom.h|  
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|此类实现`IUnknown`，并提供的默认实现[ISpecifyPropertyPages](/windows/desktop/api/ocidl/nn-ocidl-ispecifypropertypages)接口。|atlcom.h|  
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|此类提供的默认实现`ISupportErrorInfo Interface`接口，并只有一个接口生成的对象上的错误时可以使用。|atlcom.h|  
|[IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)|此接口提供用于配置的线程池的方法。|atlutil.h|  
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|此类实现`IUnknown`并提供的默认实现[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject)， [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2)，并且[IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex)接口。|atlctl.h|  
|[IWorkerThreadClient 接口](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` 是的客户端实现的接口[CWorkerThread](../../atl/reference/cworkerthread-class.md)类。|atlutil.h|  
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|此类提供包装`CreateWindow`和`CreateWindowEx`。|atlwin.h|  
|[_U_RECT](../../atl/reference/u-rect-class.md)|此参数适配器类允许`RECT`指针或引用要传递给实现方面的指针的函数。|atlwin.h|  
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|此参数适配器类允许资源名称 (LPCTSTRs) 或资源 Id （示） 要传递给函数，而无需调用方将 ID 转换为使用 MAKEINTRESOURCE 宏的字符串。|atlwin.h|  
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|此类提供一个 Windows 线程的创建函数。 如果该线程不会使用的 CRT 函数，请使用此类。|atlbase.h|  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)   
 [函数](../../atl/reference/atl-functions.md)   
 [全局变量](../../atl/reference/atl-global-variables.md)   
 [Typedef](../../atl/reference/atl-typedefs.md)   
 [类概述](../../atl/atl-class-overview.md)


