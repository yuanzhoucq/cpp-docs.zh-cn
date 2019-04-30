---
title: Platform::COMException 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 5a74184a8cbc4126988da2ba0be61d9f5b2bb71c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383342"
---
# <a name="platformcomexception-class"></a>Platform::COMException 类

表示在应用程序执行过程中发生的 COM 错误。 COMException 是一组预定义的标准异常的基类。

## <a name="syntax"></a>语法

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>成员

COMException 类从对象类以及 IException、IPrintable 和 IEquatable 接口继承。

COMException 还具有下列类型的成员。

**构造函数**

|成员|描述|
|------------|-----------------|
|[COMException](#ctor)|初始化 COMException 类的新实例。|

**方法**

COMException 类从 [Platform::Object Class](../cppcx/platform-object-class.md)继承 Equals()、Finalize(), GetHashCode()、GetType()、MemberwiseClose() 和 ToString() 方法。

**属性**

COMException 类具有以下属性。

|成员|描述|
|------------|-----------------|
|[Exception::HResult](#hresult)|与异常相对应的 HRESULT。|
|[Exception::Message](#message)|描述异常的消息。|

## <a name="derived-exceptions"></a>派生异常

下列预定义的异常从 COMException 派生。 它们与 COMException 的区别只在于名称、构造函数的名称和基础 HRESULT 值。

|名称|基础 HRESULT|描述|
|----------|------------------------|-----------------|
|COMException|*用户定义的 hresult*|从 COM 方法调用返回无法识别的 HRESULT 时引发。|
|AccessDeniedException|E_ACCESSDENIED|被拒绝访问资源或功能时引发。|
|ChangedStateException|E_CHANGED_STATE|在父集合更改后调用集合迭代器或集合视图方法，从而导致方法的结果无效时引发。|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|当 COM 类尚未注册时引发。|
|DisconnectedException|RPC_E_DISCONNECTED|当对象与其客户端的连接断开时引发。|
|FailureException|E_FAIL|操作失败时引发。|
|InvalidArgumentException|E_INVALIDARG|当提供给方法的参数之一无效时引发。|
|InvalidCastException|E_NOINTERFACE|当类型无法转换为另一种类型时引发。|
|NotImplementedException|E_NOTIMPL|当接口方法尚未在类上实现时引发。|
|NullReferenceException|E_POINTER|尝试取消引用空对象引用时引发。|
|OperationCanceledException|E_ABORT|操作中止时引发。|
|OutOfBoundsException|E_BOUNDS|某个操作尝试在有效范围外访问数据时引发。|
|OutOfMemoryException|E_OUTOFMEMORY|没有足够内存来完成操作时引发。|

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="ctor"></a> Comexception:: Comexception 构造函数

初始化 COMException 类的新实例。

### <a name="syntax"></a>语法

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>参数

*hresult*<br/>
由异常表示的错误 HRESULT。

## <a name="hresult"></a> Comexception:: Hresult 属性

与异常相对应的 HRESULT。

### <a name="syntax"></a>语法

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>属性值

一个指定错误的 HRESULT 值。

### <a name="remarks"></a>备注

有关如何解释 HRESULT 值的详细信息，请参阅[COM 错误代码的结构](/windows/desktop/com/structure-of-com-error-codes)。

## <a name="message"></a> Comexception:: Message 属性

描述异常的消息。

### <a name="syntax"></a>语法

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>属性值

异常的说明。

## <a name="see-also"></a>请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
