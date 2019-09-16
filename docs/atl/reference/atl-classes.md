---
title: ATL 类和结构 |Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498047"
---
# <a name="atl-classes-and-structs"></a>ATL 类和结构

活动模板库（ATL）包含以下类和结构。 若要按类别查找特定类，请参阅[ATL 类概述](../../atl/atl-class-overview.md)。

|类/结构|描述|标头文件|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|包含用于呈现到各种目标（如打印机、图元文件或 ActiveX 控件）的信息。|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|包含 ATL 的窗口代码中的类实例数据。|atlbase。h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|由任何使用 ATL 的项目使用。|atlbase。h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|由 ATL 中与 COM 相关的代码使用。| atlbase。h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|包含用于描述调度接口上的方法或属性的类型信息。|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|包含每个 ATL 模块使用的数据。|atlbase。h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|由 ATL 中的窗口化代码使用。|atlbase。h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|此类由字符串转换宏 CA2TEX 和 CT2AEX 以及 typedef CA2A 使用。|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|此类由字符串转换宏 CA2CTEX 和 CT2CAEX 以及 typedef CA2CA 使用。|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|此类由字符串转换宏 CA2TEX、CA2CTEX、CT2WEX、CT2CWEX 和 typedef CA2W 使用。|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|此类是访问令牌的包装器。|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|此类是 ACL （访问控制列表）结构的包装。|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|此模板用于包装一些类，这些类将 address-of 运算符重新定义为返回对象地址之外的内容。|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|此类实现数组对象。|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|此类实现线程池的单元模型 COM 服务器。|atlbase。h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|此类提供用于实现线程池单元模型 COM 服务器的方法。|atlbase。h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|此类在每个 ATL 项目中实例化。|atlcore|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|此类实现 COM 服务器模块。|atlbase。h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|此类为调试接口提供支持。|atlbase。h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|此类表示 DLL 的模块。|atlbase。h|
|[CAtlException](../../atl/reference/catlexception-class.md)|此类定义 ATL 异常。|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|此类表示应用程序的模块。|atlbase。h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|此类提供了围绕 Windows 文件处理 API 的精简包装器。|atlfile|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|此类表示内存映射文件，并向[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)的方法添加强制转换运算符。|atlfile|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|此类表示内存映射文件。|atlfile|
|[CAtlList](../../atl/reference/catllist-class.md)|此类提供用于创建和管理列表对象的方法。|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|此类提供用于创建和管理地图对象的方法。|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|此类提供多个 ATL 模块类使用的方法。|atlbase。h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|此类实现 ATL 模块。|atlbase。h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|此类是窗口的 ATL 实现，它放置在 Shell 提供的宿主窗口上以用于丰富的预览。|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|此类实现服务。|atlbase。h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|此类提供用于创建和使用临时文件的方法。|atlfile|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|此类提供内核事务管理器（KTM）函数的包装器。|atltransactionmanager.h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|此类提供对 ATL 窗口化组件的支持。|atlbase。h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|此类表示智能指针对象。|atlbase。h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|此类提供在构造智能指针数组时有用的方法。|atlbase。h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|此类提供在创建智能指针集合时有用的方法、静态函数和 typedef。|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|此类提供在构造智能指针列表时有用的方法。|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|此类表示使用向量 new 和 delete 运算符的智能指针对象。|atlbase。h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|使用向量 new 和 delete 运算符创建智能指针集合时，此类提供的方法、静态函数和 typedef 非常有用。|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|此类实现承载 ActiveX 控件的对话框（模式或无模式）。|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|此类提供用于操作承载 ActiveX 控件的窗口的方法。|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|此类提供了一些方法，用于操作承载 ActiveX 控件的窗口，并且还支持承载许可的 ActiveX 控件。|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|此类实现 `IBindStatusCallback` 接口。|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|此类为聚合的对象实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|此类提供使用 COM 内存例程管理内存的方法。|atlbase。h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|此类提供对在线程池 EXE 模块中管理单元的支持。|atlbase。h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|此类提供用于获取和释放关键节对象的所有权的方法。|atlcore|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|在 atl 7.0 中， `CComAutoThreadModule`已过时：有关更多详细信息，请参阅[ATL 模块](../../atl/atl-module-classes.md)。|atlbase。h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|此类是 Bstr 的包装器。|atlbase。h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|此类为拆卸接口实现[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|此类实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口。|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建对象。|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|此类派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|此类提供用于创建类的实例并获取其属性的方法。|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|此类提供实现复合控件所需的方法。|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|此类通过委托给所有者对象的`IUnknown`来实现 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|此类提供用于创建和管理 ATL 控件的方法。|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|此类提供用于创建和管理 ATL 控件的方法。|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|此类提供用于获取和释放关键节对象的所有权的方法。|atlcore|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|此类提供用于锁定和解锁临界区对象的方法。|atlbase。h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|此类具有用于创建和管理货币对象的方法和运算符。|atlcur。h|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|此类存储指针的`IUnknown`数组。|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|此类定义基于数组的 COM 枚举器对象。|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|此类提供 COM 枚举器接口的实现，其中所枚举的项存储在数组中。|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|此类定义基于C++标准库集合的 COM 枚举器对象。|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|此类提供与[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)相同的方法，但不提供临界区。|atlcore|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|此类提供用于处理接口指针和全局接口表（GIT）的方法。|atlbase。h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|此类使用 COM 内存分配函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|用于管理堆指针的智能指针类。|atlbase。h|
|[CComModule](../../atl/reference/ccommodule-class.md)|在 atl 7.0 中， `CComModule`已过时：有关更多详细信息，请参阅[ATL 模块](../../atl/atl-module-classes.md)。|atlbase。h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|此类提供用于递增和递减变量的值的线程安全方法。|atlbase。h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|此类提供用于递增和递减变量的值的线程安全方法，而不会锁定或解锁功能。|atlbase。h|
|[CComObject](../../atl/reference/ccomobject-class.md)|此类实现`IUnknown`非聚合对象。|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|此类管理包含`Base`对象的模块的引用计数。|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|此类实现`IUnknown`非聚合对象，但不会在构造函数中递增模块锁计数。|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|此[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的 typedef 在服务器的默认线程模型上是模板化的。|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|此类提供方法来处理非聚合对象和聚合对象的对象引用计数管理。|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|此类创建一个临时 COM 对象，并为其提供框架实现`IUnknown`。|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|此类实现`IUnknown`聚合或非聚合对象。|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|用于管理 COM 接口指针的智能指针类。|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|此类为使用基于 COM 的内存例程的智能指针类提供基础。|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|用于管理 COM 接口指针的智能指针类。|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|此类提供方法、静态函数和 typedef 在创建 COM 接口指针的集合时非常有用。|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|此类是`SAFEARRAY Data Type`结构的包装器。|atlsafe。h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|此类是`SAFEARRAYBOUND`结构的包装器。|atlsafe。h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|此类管理类[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的线程选择。|atlbase。h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|此类提供用于递增和递减变量值的方法。|atlbase。h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|此类实现一个脱离接口。|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|此类存储`IUnknown`指针，旨在用作[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)模板类的参数。|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|此类包装变量类型，并提供指示所存储数据类型的成员。|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|此类实现包含在另一个对象中的窗口。|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|此类提供使用 CRT 内存例程管理内存的方法。|atlcore|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|此类使用 CRT 堆函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|此类是 DACL （自由访问控制列表）结构的包装器。|atlsecurity.h|
|[CDebugReportHook 类](../../atl/reference/cdebugreporthook-class.md)|使用此类可将调试报告发送到命名管道。|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|此类提供两个用于在大写和小写之间转换字符的静态函数。|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|此类提供默认元素比较函数。|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|此类提供集合类的默认方法和函数。|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|此类提供用于计算哈希值的静态函数。|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|此类提供用于创建模式对话框或无模式对话框的方法。|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|此类提供支持消息映射的动态链接的方法。|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|集合类使用此类为移动、复制、比较和哈希操作提供方法和函数。|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|此类提供集合类的默认复制和移动方法。|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|此类提供用于通知容器接收器有关控件属性更改的方法。|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|此类使用 Win32 全局堆函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|此类提供用于创建和使用 handle 对象的方法。|atlbase。h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|用于管理堆指针的智能指针类。|atlcore|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|此类构成了几个智能堆指针类的基础。|atlcore|
|[CHeapPtrElementTraits 类](../../atl/reference/cheapptrelementtraits-class.md)|此类提供方法、静态函数和 typedef 在创建堆指针的集合时非常有用。|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|此类提供在构造堆指针列表时有用的方法。|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增强的位图支持，包括以 JPEG、GIF、BMP 和可移植网络图形（PNG）格式加载和保存图像的功能。|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|此类提供在构造 COM 接口指针数组时有用的方法。|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|此类提供的方法在构造 COM 接口指针的列表时很有用。|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|此类使用 Win32 本地堆函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|此类允许其他对象访问对象的消息映射。|atlwin.h|
|[CNonStatelessWorker 类](../../atl/reference/cnonstatelessworker-class.md)|接收来自线程池的请求，并将其传递到在每个请求上创建并销毁的辅助角色对象。|atlutil.h|
|[CNoWorkerThread 类](../../atl/reference/cnoworkerthread-class.md)|如果要禁用动态缓存维护，请`MonitorClass`将此类用作模板参数缓存类的参数。|atlutil.h|
|[CPathT 类](../../atl/reference/cpatht-class.md)|此类表示一个路径。|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|此类提供由基元数据类型组成的集合类的默认方法和函数。|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|此类表示私有对象安全描述符对象。|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|此类表示使用 Red-黑色二进制树的映射结构。|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|此类表示一个映射结构，该结构允许每个键与多个值相关联，同时使用 Red-黑色二进制树。|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|此类提供用于创建和使用红黑树的方法。|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|此类提供用于操作系统注册表中的项的方法。|atlbase。h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|此类为 CRT 线程提供创建函数。 如果线程将使用 CRT 函数，请使用此类。|atlbase。h|
|[CSacl](../../atl/reference/csacl-class.md)|此类是 SACL （系统访问控制列表）结构的包装器。|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|此类是`SECURITY_ATTRIBUTES`结构的精简包装器。|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|此类是`SECURITY_DESCRIPTOR`结构的包装器。|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|此类是`SID` （安全标识符）结构的包装。|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|此类提供用于管理简单数组的方法。|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|此类是[CSimpleArray](../../atl/reference/csimplearray-class.md)类的帮助器。|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|此类是[CSimpleArray](../../atl/reference/csimplearray-class.md)类的帮助器。|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|此类实现基本模式对话框。|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|此类提供对简单映射数组的支持。|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|此类是[CSimpleMap](../../atl/reference/csimplemap-class.md)类的帮助器。|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|此类是[CSimpleMap](../../atl/reference/csimplemap-class.md)类的帮助器。|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|此类提供用于实现管理单元节点对象的方法。|atlsnap|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|此类提供用于实现管理单元属性页对象的方法。|atlsnap|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|此类提供用于支持常用属性值的方法。|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|此类提供由存储`CString`对象的集合类使用的静态函数。|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|此类提供与集合类对象中存储的字符串相关的静态函数。 它类似于[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但执行不区分大小写的比较。|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|此类提供与集合类对象中存储的字符串相关的静态函数。 字符串对象作为引用处理。|atlcoll.h|
|[CThreadPool 类](../../atl/reference/cthreadpool-class.md)|此类提供处理工作项队列的工作线程池。|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|此类是`TOKEN_GROUPS`结构的包装器。|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|此类是`TOKEN_PRIVILEGES`结构的包装器。|atlsecurity.h|
|[CUrl 类](../../atl/reference/curl-class.md)|此类表示一个 URL。 它使您可以独立于其他元素处理 URL 的每个元素，无论是分析现有的 URL 字符串还是从头开始生成字符串。|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|此类由字符串转换宏 CT2AEX、CW2TEX、CW2CTEX、CT2CAEX 和 typedef CW2A 使用。|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|此类由字符串转换宏 CW2CTEX 和 CT2CWEX 以及 typedef CW2CW 使用。|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|此类由字符串转换宏 CW2TEX 和 CT2WEX 以及 typedef CW2W 使用。|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|此类使用 Win32 堆分配函数实现[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|此类提供用于操作窗口的方法。|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|此类提供用于创建或为窗口创建子类的方法。|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|此类提供了一个方法，用于标准化创建窗口对象时使用的样式。|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|此类提供了一个方法，用于标准化创建窗口对象时使用的样式。|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|此类提供用于注册窗口类的信息的方法。|atlwin.h|
|[CWorkerThread 类](../../atl/reference/cworkerthread-class.md)|此类创建一个或多个工作线程，并使用现有的工作线程，在一个或多个内核对象句柄上等待，并在其中一个句柄发出信号时执行指定的客户端函数。|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|此类表示`CreateInstance`方法的接口。|atlbase。h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|此类表示内存管理器的接口。|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|此接口提供用于指定承载的控件或容器的特性的方法。|atlbase.h，ATLIFace|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|此接口实现寄宿控件的补充环境属性。|atlbase.h，ATLIFace|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|此接口提供用于操作控件及其宿主对象的方法。|atlbase.h，ATLIFace|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|此接口提供用于操作授权控件及其宿主对象的方法。|atlbase.h，ATLIFace|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|此类提供集合类使用的方法。|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|此类实现连接点容器以管理[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象的集合。|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|此类实现连接点。|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|此类提供用于支持统一数据传输和管理连接的方法。|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|此类为`IDispatch`双重接口的部分提供默认实现。|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|此类提供`IDispatch`方法的实现。|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|此类提供`IDispatch`方法的实现，而不从类型库获取类型信息。|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Microsoft HTML 分析和呈现引擎的接口。|atlbase.h，ATLIFace|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|此类定义基于C++标准库集合的枚举器接口。|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|此类提供`IObjectSafety`接口的默认实现，以允许客户端检索和设置对象的安全级别。|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|此类提供了允许对象与其站点进行通信的方法。|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|此类提供`IOleControl`接口的默认实现并实现`IUnknown`。|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|此类提供用于协助就地控件与其容器之间的通信的方法。|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|此类实现`IUnknown`并提供使无窗口控件接收窗口消息和参与拖放操作的方法。|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|此类实现`IUnknown` ，是容器与控件进行通信时所使用的主要接口。|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|此类实现`IUnknown`并允许客户端访问对象的属性页中的信息。|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|此类实现`IUnknown`并允许对象将其属性保存到客户端提供的属性包。|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|此类实现[IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)接口。|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|此类实现`IUnknown`并提供[IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)接口的默认实现。|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|此类实现`IUnknown`和[IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)接口方法。|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|此类公开[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口作为可连接对象上的传出接口。|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|此类实现`IUnknown`并继承[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现。|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|此类实现`IUnknown`并提供[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)接口的默认实现。|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|此类提供[IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)和[IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)方法的默认实现。|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|此类将容器的控件初始化组合为单个调用。|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|此类实现`IUnknown`并提供[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)接口的默认实现。|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|此类提供`IServiceProvider`接口的默认实现。|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|此类实现`IUnknown`并提供[ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)接口的默认实现。|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|此类提供`ISupportErrorInfo Interface`接口的默认实现，并且可在只有单个接口在对象上生成错误时使用。|atlcom.h|
|[IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)|此接口提供用于配置线程池的方法。|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|此类实现`IUnknown`并提供[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)接口的默认实现。|atlctl.h|
|[IWorkerThreadClient 接口](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`是由[CWorkerThread](../../atl/reference/cworkerthread-class.md)类的客户端实现的接口。|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|此类提供和`CreateWindow` `CreateWindowEx`的包装。|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|此参数适配器类允许`RECT`将指针或引用传递给在指针方面实现的函数。|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|使用此参数适配器类，可以将资源名称（LPCTSTRs）或资源 Id （UINTs）传递给函数，而无需调用方使用 MAKEINTRESOURCE 宏将 ID 转换为字符串。|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|此类提供 Windows 线程的创建功能。 如果线程不使用 CRT 函数，请使用此类。|atlbase。h|

## <a name="see-also"></a>请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)<br/>
[函数](../../atl/reference/atl-functions.md)<br/>
[全局变量](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[类概述](../../atl/atl-class-overview.md)
