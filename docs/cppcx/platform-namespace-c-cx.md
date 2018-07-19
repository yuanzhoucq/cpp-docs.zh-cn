---
title: 平台命名空间 (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- Platform/Platform
dev_langs:
- C++
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 348bedcde953cbcd6084023d6f7117c7f7f001f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091954"
---
# <a name="platform-namespace-ccx"></a>Platform 命名空间 (C++/CX)
包含与 Windows 运行时兼容的内置类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
using namespace Platform;  
```  
  
### <a name="members"></a>成员  
 **特性**  
  
 平台命名空间包含特性、类、枚举、接口和结构。 平台还包含嵌套的命名空间。  
  
|特性|描述|  
|---------------|-----------------|  
|Flags|指示可将枚举视为位域（即一组标志）。|  
|MTAThread|指示应用程序的线程处理模型为多线程单元 (MTA)。|  
|STAThread|指示应用程序的线程模型是单线程单元 (STA)。|  
  
 **类**  
  
 平台命名空间具有以下类。  
  
|类|描述|  
|-----------|-----------------|  
|[Platform::AccessDeniedException 类](../cppcx/platform-accessdeniedexception-class.md)|被拒绝访问资源或功能时引发。|  
|[Platform::Agile 类](../cppcx/platform-agile-class.md)|表示非敏捷对象为敏捷对象。|  
|[Platform::Array 类](../cppcx/platform-array-class.md)|表示一维可修改数组。|  
|[Platform::ArrayReference 类](../cppcx/platform-arrayreference-class.md)|表示一个其初始化被优化以最小化复制操作的数组。|  
|[Platform::Box 类](../cppcx/platform-box-class.md)|用于声明一个封装值类型（如 Windows::Foundation::DateTime 或 int64）的装箱类型（当该类型在应用程序二进制接口 (ABI) 之间传递或在类型为 [Platform::Object^](../cppcx/platform-object-class.md)的变量中存储时）。|  
|[Platform::ChangedStateException 类](../cppcx/platform-changedstateexception-class.md)|在父集合更改后调用集合迭代器或集合视图方法，从而导致方法的结果无效时引发。|  
|[Platform::ClassNotRegisteredException 类](../cppcx/platform-classnotregisteredexception-class.md)|当 COM 类尚未注册时引发。|  
|[Platform::COMException 类](../cppcx/platform-comexception-class.md)|表示从 COM 方法调用返回无法识别的值时引发的异常。|  
|[Platform::Delegate 类](../cppcx/platform-delegate-class.md)|表示回调函数的签名。|  
|[Platform::DisconnectedException 类](../cppcx/platform-disconnectedexception-class.md)|该对象已与其客户端断开连接。|  
|[Platform::Exception 类](../cppcx/platform-exception-class.md)|表示在应用程序执行过程中发生的错误。 异常的基类。|  
|[Platform::FailureException 类](../cppcx/platform-failureexception-class.md)|操作失败时引发。 它是 E_FAIL HRESULT 的等效项。|  
|[Platform::Guid 值类](../cppcx/platform-guid-value-class.md)|代表 Windows 运行时类型系统中的 GUID。|  
|[Platform::InvalidArgumentException 类](../cppcx/platform-invalidargumentexception-class.md)|当提供给方法的参数之一无效时引发。|  
|[Platform::InvalidCastException 类](../cppcx/platform-invalidcastexception-class.md)|当强制转换或显式转换无效时引发。|  
|[Platform::MTAThreadAttribute 类](../cppcx/platform-mtathreadattribute-class.md)|指示应用程序的线程处理模型为多线程单元 (MTA)。|  
|[Platform::NotImplementedException 类](../cppcx/platform-notimplementedexception-class.md)|当接口方法尚未在类上实现时引发。|  
|[Platform::NullReferenceException 类](../cppcx/platform-nullreferenceexception-class.md)|尝试取消引用空对象引用时引发。|  
|[Platform::Object 类](../cppcx/platform-object-class.md)|提供常见行为的基类。|  
|[Platform::ObjectDisposedException 类](../cppcx/platform-objectdisposedexception-class.md)|对已释放对象执行操作时引发。|  
|[Platform::OperationCanceledException 类](../cppcx/platform-operationcanceledexception-class.md)|操作中止时引发。|  
|[Platform::OutOfBoundsException 类](../cppcx/platform-outofboundsexception-class.md)|某个操作尝试在有效范围外访问数据时引发。|  
|[Platform::OutOfMemoryException 类](../cppcx/platform-outofmemoryexception-class.md)|没有足够内存来完成操作时引发。|  
|[Platform::STAThreadAttribute 类](../cppcx/platform-stathreadattribute-class.md)|指示应用程序的线程模型是单线程单元 (STA)。|  
|[Platform::String 类](../cppcx/platform-string-class.md)|用于表示文本的 Unicode 字符的有序集合。|  
|[Platform::StringReference 类](../cppcx/platform-stringreference-class.md)|提供对字符串缓冲区的访问并最大限度减少复制开销。|  
|[Platform::Type 类](../cppcx/platform-type-class.md)|通过类别枚举标识内置类型。|  
|[Platform::ValueType 类](../cppcx/platform-valuetype-class.md)|值类型实例的基类。|  
|[Platform::WeakReference 类](../cppcx/platform-weakreference-class.md)|提供对 ref 类对象的弱引用，该引用不递增引用计数。|  
|[Platform::WriteOnlyArray 类](../cppcx/platform-writeonlyarray-class.md)|表示在实现 FillArray 模式的方法中用作输入参数的一维只写数组。|  
|[Platform::WrongThreadException 类](../cppcx/platform-wrongthreadexception-class.md)|当一个线程通过专用于代理对象而不属于该线程单元的接口指针调用时引发。|  
  
 **接口实现**  
  
 该平台命名空间定义以下接口。  
  
|接口|描述|  
|---------------|-----------------|  
|[Platform::IBox 接口](../cppcx/platform-ibox-interface.md)|用于将值类型传递给其参数被类型化为 Platform::Object^ 的函数。|  
|[Platform::IBoxArray 接口](../cppcx/platform-iboxarray-interface.md)|用于将值类型数组传递给其参数被类型化为 Platform::Array 的函数的接口。|  
|[Platform::IDisposable 接口](../cppcx/platform-idisposable-interface.md)|用于释放非托管资源。|  
  
 **枚举**  
  
 该平台命名空间具有以下枚举。  
  
|接口|描述|  
|---------------|-----------------|  
|[Platform::CallbackContext 枚举](../cppcx/platform-callbackcontext-enumeration.md)|用作委托构造函数的参数的枚举。 它确定是将回调封送到起始线程还是调用方线程。|  
|[Platform::TypeCode 枚举](../cppcx/platform-typecode-enumeration.md)|指定表示一个内置类型的数字类别。|  
  
 **结构**  
  
 该平台命名空间具有以下结构。  
  
|结构|描述|  
|---------------|-----------------|  
|[Platform::Enum 类](../cppcx/platform-enum-class.md)|表示一个命名常量。|  
|[Platform::Guid 值类](../cppcx/platform-guid-value-class.md)|表示一个 GUID。|  
|[Platform::IntPtr 值类](../cppcx/platform-intptr-value-class.md)|其大小适合平台（32 位或 64 位）的带符号指针。|  
|[Platform::SizeT 值类](../cppcx/platform-sizet-value-class.md)|用于表示对象大小的无符号数据类型。|  
|[Platform::UIntPtr 值类](../cppcx/platform-uintptr-value-class.md)|其大小适合平台（32 位或 64 位）的无符号指针。|  
  
## <a name="see-also"></a>请参阅  
 [Platform:: collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Platform::Runtime::CompilerServices Namespace](../cppcx/platform-runtime-compilerservices-namespace.md)   
 [Platform::Runtime::InteropServices Namespace](../cppcx/platform-runtime-interopservices-namespace.md)   
 [Platform::Metadata 命名空间](../cppcx/platform-metadata-namespace.md)