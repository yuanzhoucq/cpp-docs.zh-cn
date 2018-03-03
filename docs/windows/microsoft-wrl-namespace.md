---
title: "Microsoft:: wrl Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
dev_langs:
- C++
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 64c8b82320e0b402c06432438cd49a23be5d1f2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL 命名空间
定义构成 Windows 运行时 c + + 模板库的基础类型。  
  
## <a name="syntax"></a>语法  
  
```  
namespace Microsoft::WRL;  
```  
  
## <a name="members"></a>成员  
  
### <a name="typedefs"></a>Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[ActivationFactory 类](../windows/activationfactory-class.md)|启用 Windows 运行时将激活的一个或多个类。|  
|[AsyncBase 类](../windows/asyncbase-class.md)|实现 Windows 运行时异步状态机。|  
|[ClassFactory 类](../windows/classfactory-class.md)|实现 `IClassFactory` 接口的基本功能。|  
|[ComPtr 类](../windows/comptr-class.md)|创建表示模板参数指定的接口的 *智能指针* 类型。 ComPtr 会自动维护基础接口指针的引用计数，并在引用计数变为零时释放接口。|  
|[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)|一种用于延迟的事件自变量类型的模板类。|  
|[EventSource 类](../windows/eventsource-class.md)|表示一个事件。 `EventSource` 成员函数将添加、删除和调用事件处理程序。|  
|[FtmBase 类](../windows/ftmbase-class.md)|表示自由线程封送拆收器对象。|  
|[Module 类](../windows/module-class.md)|表示相关对象的集合。|  
|[RuntimeClass 类](../windows/runtimeclass-class.md)|表示继承指定数量的接口的实例化类，并提供指定 Windows 运行时、经典 COM 和弱引用支持。|  
|[SimpleActivationFactory 类](../windows/simpleactivationfactory-class.md)|提供创建 Windows 运行时或经典 COM 基类的基础机制。|  
|[SimpleClassFactory 类](../windows/simpleclassfactory-class.md)|提供创建基类的基本机制。|  
|[WeakRef 类](../windows/weakref-class.md)|表示只能由 Windows 运行时而不是经典 COM 使用的 *弱引用* 。 弱引用表示可能可访问或可能不可访问的对象。|  
  
### <a name="structures"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|[ChainInterfaces 结构](../windows/chaininterfaces-structure.md)|指定可应用于一组接口 ID 的验证和初始化函数。|  
|[CloakedIid 结构](../windows/cloakediid-structure.md)|指示无法访问 IID 列表中指定接口的 RuntimeClass、Implements 和 ChainInterfaces 模板。|  
|[Implements 结构](../windows/implements-structure.md)|为指定接口实现 QueryInterface 和 GetIid。|  
|[MixIn 结构](../windows/mixin-structure.md)|确保运行时类先后派生自 Windows 运行时接口（如果有）和经典 COM 接口。|  
|[RuntimeClassFlags 结构](../windows/runtimeclassflags-structure.md)|包含的实例类型[RuntimeClass](../windows/runtimeclass-class.md)。|  
  
### <a name="enumerations"></a>枚举  
  
|name|描述|  
|----------|-----------------|  
|[AsyncResultType 枚举](../windows/asyncresulttype-enumeration.md)|指定 GetResults() 方法返回的结果类型。|  
|[ModuleType 枚举](../windows/moduletype-enumeration.md)|指定模块是否应支持进程内服务器或进程外服务器。|  
|[RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)|指定的一种[RuntimeClass](../windows/runtimeclass-class.md)支持的实例。|  
  
### <a name="functions"></a>函数  
  
|名称|描述|  
|----------|-----------------|  
|[AsWeak 函数](../windows/asweak-function.md)|检索对指定实例的弱引用。|  
|[回调函数](../windows/callback-function-windows-runtime-cpp-template-library.md)|创建一个对象，该对象的成员函数是一个回调方法。|  
|[CreateActivationFactory 函数](../windows/createactivationfactory-function.md)|创建为可由 Windows 运行时激活的指定类生成实例的工厂。|  
|[CreateClassFactory 函数](../windows/createclassfactory-function.md)|创建为指定类生成实例的工厂。|  
|[Make 函数](../windows/make-function.md)|初始化指定的 Windows 运行时类。|  
  
## <a name="requirements"></a>惠?  
 **标头：** async.h、 client.h、 corewrappers.h、 event.h、 ftm.h、 implements.h、 internal.h、 module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)