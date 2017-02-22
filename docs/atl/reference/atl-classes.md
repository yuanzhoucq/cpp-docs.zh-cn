---
title: "ATL 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 类"
  - "类 [C++], ATL"
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# ATL 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

活动模板库 \(ATL\) 包括以下选件类。  若要按类别查找特定选件类，请参见 [ATL选件类概述](../../atl/atl-class-overview.md)。  
  
|类|说明|标头文件|  
|-------|--------|----------|  
|[CA2AEX](../../atl/reference/ca2aex-class.md)|字符串翻译宏 `CA2TEX` 和 `CT2AEX`和typedef使用此选件类 **CA2A**。|atlconv.h|  
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|字符串翻译宏 `CA2CTEX` 和 `CT2CAEX`和typedef使用此选件类 **CA2CA**。|atlconv.h|  
|[CA2WEX](../../atl/reference/ca2wex-class.md)|字符串翻译宏使用此选件类 `CA2TEX`、 `CA2CTEX`、 `CT2WEX`和 `CT2CWEX`和typedef **CA2W**。|atlconv.h|  
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|此选件类是访问令牌的包装。|atlsecurity.h|  
|[CAcl](../../atl/reference/cacl-class.md)|此选件类是 **ACL** \(访问控制列表\)机制的包装。|atlsecurity.h|  
|[CAdapt](../../atl/reference/cadapt-class.md)|此模板用于包装除了对象的地址以外，重新定义address\-of运算符返回其上的选件类。|atlcomcli.h|  
|[CAtlArray](../../atl/reference/catlarray-class.md)|此选件类实现数组对象。|atlcoll.h|  
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|此选件类实现一线程池，单元模型COM服务器。|atlbase.h|  
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|此选件类为实现线程池提供方法，单元模型COM服务器。|atlbase.h|  
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|此选件类在每个ATL项目实例化。|atlcore.h|  
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|此选件类实现一个COM服务器模块。|atlbase.h|  
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|此选件类提供调试接口支持。|atlbase.h|  
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|此选件类表示DLL的模块。|atlbase.h|  
|[CAtlException](../../atl/reference/catlexception-class.md)|此选件类定义了ATL异常。|atlexcept.h|  
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|此选件类表示应用程序的模块。|atlbase.h|  
|[CAtlFile](../../atl/reference/catlfile-class.md)|此选件类文件中处理API的Windows周围提供一个瘦包装。|atlfile.h|  
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|此选件类表示一个内存映射文件，添加转换运算符将 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)方法。|atlfile.h|  
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|此选件类表示一个内存映射文件。|atlfile.h|  
|[CAtlList](../../atl/reference/catllist-class.md)|此选件类为创建和管理列表对象的方法。|atlcoll.h|  
|[CAtlMap](../../atl/reference/catlmap-class.md)|此选件类为创建和管理映射对象的方法。|atlcoll.h|  
|[CAtlModule](../../atl/reference/catlmodule-class.md)|此选件类提供了若干ATL模块选件类的方法。|atlbase.h|  
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|此选件类实现一个ATL模块。|atlbase.h|  
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|此选件类是在Shell提供的宿主窗口放置为丰富预览窗口的ATL实现。|atlpreviewctrlimpl.h|  
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|此选件类实现一服务。|atlbase.h|  
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|此选件类提供对临时文件的创建和使用。|atlfile.h|  
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|此选件类提供一个包装为核心事务管理器\(KTM\)功能。|atltransactionmanager.h|  
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|此选件类提供ATL多窗口元素支持。|atlbase.h|  
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|此选件类表示智能指针对象。|atlbase.h|  
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|当构造一个数组智能指针时，此选件类提供有用的方法。|atlbase.h|  
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|在创建智能指针时的集合，此选件类的方法、静态有用功能和的typedef。|atlcoll.h|  
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|当构造列出了智能指针时，此选件类提供有用的方法。|atlcoll.h|  
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|使用新的向量和删除运算符，此选件类表示智能指针对象。|atlbase.h|  
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|在创建智能指针使用新的向量和删除运算符时的集合，此选件类的方法、静态有用功能和的typedef。|atlcoll.h|  
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|此选件类实现一个对话框\(模式或无模式\)承载ActiveX控件。|atlwin.h|  
|[CAxWindow](../../atl/reference/caxwindow-class.md)|提供用于承载ActiveX控件的选件此类用于操作窗口。|atlwin.h|  
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|此选件类用于操作承载一个ActiveX控件并为承载授权的ActiveX控件支持的windows提供方法。|atlwin.h|  
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|此类实现 `IBindStatusCallback` 接口。|atlctl.h|  
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|此选件类实现一个复合对象的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。|atlcom.h|  
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|使用COM内存实例，此选件类用于管理内存的方法。|atlbase.h|  
|[CComApartment](../../atl/reference/ccomapartment-class.md)|此选件类提供用于管理在一个线程池的EXE模块的一个单元支持。|atlbase.h|  
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|此选件类来获取和释放一临界区对象的所有权的方法。|atlcore.h|  
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|自ATL 7.0，`CComAutoThreadModule` 已过时:有关详细信息 [ATL模块](../../atl/atl-module-classes.md) 参见。|atlbase.h|  
|[CComBSTR](../../atl/reference/ccombstr-class.md)|此选件类是 `BSTR`的s.包装。|atlbase.h|  
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|此选件类实现拖曳接口的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。|atlcom.h|  
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|此选件类实现 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 接口。|atlcom.h|  
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|此选件类实现 [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) 接口。|atlcom.h|  
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|此选件类在多个单元 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) 实现接口并允许对象创建的。|atlcom.h|  
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|此选件类从 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 派生并使用 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 构造一个对象。|atlcom.h|  
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|此选件类用于创建选件类的实例并获取其属性的方法。|atlcom.h|  
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|此选件类提供需要的方法实现复合控件。|atlctl.h|  
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|此选件类通过委托实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 对所有者对象的 **IUnknown**。|atlcom.h|  
|[CComControl](../../atl/reference/ccomcontrol-class.md)|此选件类为创建和管理ATL控件的方法。|atlctl.h|  
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|此选件类为创建和管理ATL控件的方法。|atlctl.h|  
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|此选件类来获取和释放一临界区对象的所有权的方法。|atlcore.h|  
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|此选件类为锁定和取消锁定临界区对象的方法。|atlbase.h|  
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|此选件类具有方法和运算符创建并管理的 `CURRENCY` 对象。|atlcur.h|  
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|此选件类存储数组 **IUnknown** 指针。|atlcom.h|  
|[CComEnum](../../atl/reference/ccomenum-class.md)|此选件类定义了基于数组的COM enumerator对象。|atlcom.h|  
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|此选件类对枚举项存储在数组中的COM枚举器提供了接口实现。|atlcom.h|  
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|此选件类定义了基于STL集合的COM enumerator对象。|atlcom.h|  
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|此选件类的方法和 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 相同，但不提供临界区。|atlcore.h|  
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|此选件类为相关的方法接口指针和全局接口表\(GIT）。|atlbase.h|  
|[CComHeap](../../atl/reference/ccomheap-class.md)|使用COM内存分配的分配函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。|ATLComMem.h|  
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|托管堆指针的智能指针选件类。|atlbase.h|  
|[CComModule](../../atl/reference/ccommodule-class.md)|自ATL 7.0，`CComModule` 已过时:有关详细信息 [ATL模块](../../atl/atl-module-classes.md) 参见。|atlbase.h|  
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|此选件类为递增和递减变量的值提供线程安全的方法。|atlbase.h|  
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|此选件类为递增和递减变量的值提供线程安全的方法，即，不使用锁或打开功能的临界区。|atlbase.h|  
|[CComObject](../../atl/reference/ccomobject-class.md)|此选件类实现一nonaggregated对象的 **IUnknown**。|atlcom.h|  
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|此选件类管理在包含您的 `Base` 对象的模块的引用数。|atlcom.h|  
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|此选件类实现一nonaggregated对象的 **IUnknown**，但是，不会使在构造函数的模块锁计数。|atlcom.h|  
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 此typedef在服务器的默认线程模型templatized。|atlcom.h|  
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|此选件类提供了处理对象引用nonaggregated和聚合的对象的计数管理。|atlcom.h|  
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|此选件类创建一个临时COM对象并为其提供 **IUnknown**的一个骨骼实现。|atlcom.h|  
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|此选件类实现合成或nonaggregated对象的 **IUnknown**。|atlcom.h|  
|[CComPtr](../../atl/reference/ccomptr-class.md)|托管COM接口指针的智能指针选件类。|atlcomcli.h|  
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|使用基于COM的内存实例，此选件类为智能指针选件类提供基础。|atlcomcli.h|  
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|托管COM接口指针的智能指针选件类。|atlcomcli.h|  
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|在创建COM接口指针时的集合，此选件类的方法、静态有用功能和的typedef。|atlcoll.h|  
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|此选件类是 `SAFEARRAY Data Type` 结构的包装。|atlsafe.h|  
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|此选件类是 `SAFEARRAYBOUND` 结构的包装。|atlsafe.h|  
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|此选件类管理选件类的 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)线程选择。|atlbase.h|  
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|此选件类为递增和递减变量的值的方法。|atlbase.h|  
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|此选件类实现一拖曳接口。|atlcom.h|  
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|此选件类存储 **IUnknown** 指针和旨在用作参数 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 模板选件类。|atlcom.h|  
|[CComVariant](../../atl/reference/ccomvariant-class.md)|此选件类包装种类型，提供指示数据类型的成员存储。|atlcomcli.h|  
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|此选件类实现在其他对象中包含的窗口。|atlwin.h|  
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|使用CRT内存实例，此选件类用于管理内存的方法。|atlcore.h|  
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|使用CRT堆函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。|atlmem.h|  
|[CDacl](../../atl/reference/cdacl-class.md)|此选件类是DACL \(自由访问控制列表\)结构的包装。|atlsecurity.h|  
|[CDebugReportHook Class](../../atl/reference/cdebugreporthook-class.md)|使用此选件类发送调试报告为命名管道。|atlutil.h|  
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|此选件类为将在大写和小写之间的字符提供两个静态函数。|atlcoll.h|  
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|此选件类提供默认元素比较函数。|atlcoll.h|  
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|此选件类提供默认方法，并收集的功能类别。|atlcoll.h|  
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|此选件类用于计算哈希值提供静态函数。|atlcoll.h|  
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|此选件类为创建模式或无模式对话框的方法。|atlwin.h|  
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|此选件类提供支持动态绑定消息映射的方法。|atlwin.h|  
|[CElementTraits](../../atl/reference/celementtraits-class.md)|集合选件类用于此选件类为移动，复制，比较和散列的操作的方法和功能。|atlcoll.h|  
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|此选件类提供默认副本，并且集合的移动方案类别。|atlcoll.h|  
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|此选件类用于通知控件属性的更改容器的接收器的方法。|atlctl.h|  
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|使用Win32全局堆函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。|atlmem.h|  
|[CHandle](../../atl/reference/chandle-class.md)|此选件类提供创建和使用处理对象。|atlbase.h|  
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|托管堆指针的智能指针选件类。|atlcore.h|  
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|此选件类窗体进行一些智能堆指针选件类的基础。|atlcore.h|  
|[CHeapPtrElementTraits选件类](../../atl/reference/cheapptrelementtraits-class.md)|在创建堆指针时的集合，此选件类的方法、静态有用功能和的typedef。|atlcoll.h|  
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|当构造列表堆指针时，此选件类提供有用的方法。|atlcoll.h|  
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供在JPEG、GIF、BMP和可移植网络映像\(PNG\)格式的增强支持位图，包括能够加载和保存图像。|atlimage.h|  
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|当构造一个数组COM接口指针时，此选件类提供有用的方法。|atlcoll.h|  
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|当构造列表COM接口指针时，此选件类提供有用的方法。|atlcoll.h|  
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|使用Win32本地堆函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。|atlmem.h|  
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|此选件类允许对象的消息映射被其他对象访问。|atlwin.h|  
|[CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md)|接收来自线程池的请求并传递到在每个请求创建和销毁的辅助对象。|atlutil.h|  
|[CNoWorkerThread Class](../../atl/reference/cnoworkerthread-class.md)|如果想要禁用动态缓存维护，请使用此选件类作为参数。`MonitorClass` 模板参数缓存选件类。|atlutil.h|  
|[CPathT Class](../../atl/reference/cpatht-class.md)|此选件类表示路径。|atlpath.h|  
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|此选件类为集合选件类提供默认方法和函数中对基元数据类型。|atlcoll.h|  
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|此选件类表示私有对象安全说明符的对象。|atlsecurity.h|  
|[CRBMap](../../atl/reference/crbmap-class.md)|使用红色黑色二叉树，此选件类表示一个映射的结构。|atlcoll.h|  
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|使用红色黑色二叉树，此选件类表示允许每个键与多个值的映射，结构。|atlcoll.h|  
|[CRBTree](../../atl/reference/crbtree-class.md)|此选件类是创建和使用红色黑色树的方法。|atlcoll.h|  
|[CRegKey](../../atl/reference/cregkey-class.md)|此选件类为操作系统注册表的项的方法。|atlbase.h|  
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|此选件类。CRT线程提供创建功能。  如果线程将使用CRT函数，请使用此选件类。|atlbase.h|  
|[CSacl](../../atl/reference/csacl-class.md)|此选件类是SACL \(系统访问控制列表\)结构的包装。|atlsecurity.h|  
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|此选件类是 **SECURITY\_ATTRIBUTES** 结构的一个瘦包装。|atlsecurity.h|  
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|此选件类是 **SECURITY\_DESCRIPTOR** 结构的包装。|atlsecurity.h|  
|[CSid](../../atl/reference/csid-class.md)|此选件类是 `SID` \(安全标识符\)机制的包装。|atlsecurity.h|  
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|此选件类用于管理一个简单数组的方法。|atlsimpcoll.h|  
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|此选件类是 [CSimpleArray](../../atl/reference/csimplearray-class.md) 选件类的一个帮助器。|atlsimpcoll.h|  
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|此选件类是 [CSimpleArray](../../atl/reference/csimplearray-class.md) 选件类的一个帮助器。|atlsimpcoll.h|  
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|此选件类实现基本模式对话框。|atlwin.h|  
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|此选件类提供一个简单的映射数组支持。|atlsimpcoll.h|  
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|此选件类是 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类的一个帮助器。|atlsimpcoll.h|  
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|此选件类是 [CSimpleMap](../../atl/reference/csimplemap-class.md) 选件类的一个帮助器。|atlsimpcoll.h|  
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|此选件类为实现管理单元节点对象的方法。|atlsnap.h|  
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|此选件类为实现管理单元属性页对象的方法。|atlsnap.h|  
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|此选件类支持常用属性值的方法。|atlctl.h|  
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|此选件类提供集合选件使用类的静态函数存储 `CString` 对象。|cstringt.h|  
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|此选件类提供静态函数与集合选件类对象存储的字符串相关。  它类似于 [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但是，执行不区分大小写的比较。|atlcoll.h|  
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|此选件类提供静态函数与集合选件类对象存储的字符串相关。  字符串对象处理引用。|atlcoll.h|  
|[CThreadPool选件类](../../atl/reference/cthreadpool-class.md)|此选件类提供的辅助线程池处理工作项队列。|atlutil.h|  
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|此选件类是 **TOKEN\_GROUPS** 结构的包装。|atlsecurity.h|  
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|此选件类是 **TOKEN\_PRIVILEGES** 结构的包装。|atlsecurity.h|  
|[CUrl Class](../../atl/reference/curl-class.md)|此选件类表示URL。  它是否可以独立于其他操作URL的每个元素分析现有的URL字符串或从头开始生成字符串。|atlutil.h|  
|[CW2AEX](../../atl/reference/cw2aex-class.md)|字符串翻译宏使用此选件类 `CT2AEX`、 `CW2TEX`、 `CW2CTEX`和 `CT2CAEX`和typedef **CW2A**。|atlconv.h|  
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|字符串翻译宏 `CW2CTEX` 和 `CT2CWEX`和typedef使用此选件类 **CW2CW**。|atlconv.h|  
|[CW2WEX](../../atl/reference/cw2wex-class.md)|字符串翻译宏 `CW2TEX` 和 `CT2WEX`和typedef使用此选件类 `CW2W`。|atlconv.h|  
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|使用Win32堆分配函数，此选件类实现 [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。|atlmem.h|  
|[CWindow](../../atl/reference/cwindow-class.md)|此选件类用于操作窗口的方法。|atlwin.h|  
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|此选件类用于创建或subclassing窗口的方法。|atlwin.h|  
|[CWinTraits](../../atl/reference/cwintraits-class.md)|在创建windows对象时，此选件类出于标准化使用的样式提供方法。|atlwin.h|  
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|在创建windows对象时，此选件类出于标准化使用的样式提供方法。|atlwin.h|  
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|此选件类提供注册窗口选件类的信息的方法。|atlwin.h|  
|[CWorkerThread Class](../../atl/reference/cworkerthread-class.md)|当其中一个处理事件信号时，此选件类在一个或多个核心对象处理创建辅助线程或使用现有工作项，等待，并执行一个指定的客户端功能。|atlutil.h|  
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|此选件类表示接口访问 `CreateInstance` 方法。|atlbase.h|  
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|此选件类表示界面内存管理器。|atlmem.h|  
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|此接口指定承载的控件或容器的属性的方法。|atlbase.h，ATLIFace.h|  
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|此接口实现一个承载的控件的补充环境属性。|atlbase.h，ATLIFace.h|  
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|此接口用于操作控件与其宿主对象的方法。|atlbase.h，ATLIFace.h|  
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|此接口用于操作一个授权控件与其宿主对象的方法。|atlbase.h，ATLIFace.h|  
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|此选件类提供集合选件类的方法。|atlcom.h|  
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|此选件类实现连接点容器管理 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 对象的集合。|atlcom.h|  
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|此选件类实现连接点。|atlcom.h|  
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|此选件类支持合并数据传输和管理连接的方法。|atlctl.h|  
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|此选件类为双重接口的 `IDispatch` 部分提供默认实现。|atlcom.h|  
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|此选件类提供 `IDispatch` 方法的实现。|atlcom.h|  
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|此选件类提供 `IDispatch` 方法的实现，这样，而不会获得类型信息从类型库。|atlcom.h|  
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|对分析和呈现引擎的Microsoft HTML的接口。|atlbase.h，ATLIFace.h|  
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|此选件类定义了基于STL集合的枚举数接口。|atlcom.h|  
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|此选件类提供 `IObjectSafety` 接口的默认实现允许客户端检索和设置对象的安全级别。|atlctl.h|  
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|此选件类的方法允许对象与其站点通信。|atlcom.h|  
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|此选件类提供 **IOleControl** 接口的默认实现\)和实现 **IUnknown**。|atlctl.h|  
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|此选件类用于协助一个就地控件与其容器之间的通信的方法。|atlctl.h|  
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|此选件类实现 **IUnknown** 并提供使无窗口控件接收windows消息和参与拖放操作的方法。|atlctl.h|  
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|此选件类实现 **IUnknown** 是容器与控件进行通信的主体接口。|atlctl.h|  
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|此选件类实现 **IUnknown** 并将客户端来访问对象中的属性页的信息。|atlctl.h|  
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|此选件类实现 **IUnknown** 并允许对象保存其属性设置为一个由客户端提供的属性包。|atlcom.h|  
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|此选件类实现 [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) 接口。|atlcom.h|  
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|此选件类实现 **IUnknown** 并提供 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) 接口的默认实现。|atlcom.h|  
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|此选件类执行 **IUnknown** 和 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712) 接口方法。|atlctl.h|  
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|此选件类公开 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 接口标记为可连接对象的一个输出接口。|atlctl.h|  
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|此选件类实现 **IUnknown** 和继承 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)的默认实现。|atlctl.h|  
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|此选件类实现 **IUnknown** 并提供 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 接口的默认实现。|atlctl.h|  
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|此选件类提供 [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) 和 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) 方法的默认实现。|atlcom.h|  
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|此选件类组合容器的控件初始化为一个调用。|atlctl.h|  
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|此选件类实现 **IUnknown** 并提供 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) 接口的默认实现。|atlctl.h|  
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|此选件类提供 `IServiceProvider` 接口的默认实现。|atlcom.h|  
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|此选件类实现 **IUnknown** 并提供 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) 接口的默认实现。|atlcom.h|  
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|只有一个接口在对象时，发生此错误选件类提供 `ISupportErrorInfo Interface` 接口的默认实现\)，可以使用。|atlcom.h|  
|[IThreadPoolConfig接口](../../atl/reference/ithreadpoolconfig-interface.md)|此接口用于配置线程池的方法。|atlutil.h|  
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|此选件类实现 **IUnknown** 并提供 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)、 [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)和 [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) 接口的默认实现。|atlctl.h|  
|[IWorkerThreadClient Interface](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient` 是 [CWorkerThread](../../atl/reference/cworkerthread-class.md) 选件类的客户端实现的接口。|atlutil.h|  
|[\_U\_MENUorID](../../atl/reference/u-menuorid-class.md)|此选件类。**CreateWindow** 和 **CreateWindowEx**提供包装。|atlwin.h|  
|[\_U\_RECT](../../atl/reference/u-rect-class.md)|此参数适配器选件类允许 `RECT` 指针或引用传递给实现基于指针的函数。|atlwin.h|  
|[\_U\_STRINGorID](../../atl/reference/u-stringorid-class.md)|此参数适配器选件类允许资源名称\(`LPCTSTR`属于\)或资源ID \(**UINT**属于\)使用 **MAKEINTRESOURCE** 宏，将传递给函数，而无需调用方ID转换为字符串。|atlwin.h|  
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|此选件类对于Windows线程提供创建功能。  如果线程不使用CRT函数，请使用此选件类。|atlbase.h|  
  
## 请参阅  
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)   
 [函数](../../atl/reference/atl-functions.md)   
 [Global Variables](../../atl/reference/atl-global-variables.md)   
 [结构](../../atl/reference/atl-structures.md)   
 [Typedefs](../../atl/reference/atl-typedefs.md)   
 [Class Overview](../../atl/atl-class-overview.md)