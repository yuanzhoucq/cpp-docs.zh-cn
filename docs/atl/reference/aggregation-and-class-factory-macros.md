---
title: 聚合和类工厂宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 38239942b99a29b5777deef8000d9f1ab85b10e6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862596"
---
# <a name="aggregation-and-class-factory-macros"></a>聚合和类工厂宏

这些宏提供控制聚合和声明类工厂的方法。

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|声明您的对象可以聚合（默认值）。|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)类工厂声明为 ATL 默认类工厂。|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|将类工厂对象声明为类工厂。|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|将[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)声明为类工厂。|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|将[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)声明为类工厂。|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|将[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)声明为类工厂。|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|声明虚拟 `GetControllingUnknown` 函数。|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|声明无法聚合您的对象。|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|声明必须聚合您的对象。|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|检查外部未知的值，并根据需要将对象声明为可聚合或不可聚合。|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|保护外部对象在构造内部对象的过程中不会被删除。|
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定容器的 VIEWSTATUS 标志。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE

指定可以聚合对象。

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
中要定义为可聚合的类的名称。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含用于指定默认聚合模型的宏。 若要重写此默认值，请在类定义中指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)声明为类工厂。

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)使用此宏为对象声明默认类工厂。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

##  <a name="ccomclassfactory_class"></a>CComClassFactory 类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>备注

`CComClassFactory` 实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，该接口包含用于创建特定 CLSID 对象的方法，以及在内存中锁定类工厂以允许更快地创建新对象。 必须为在系统注册表中注册的每个类实现 `IClassFactory`，并为其分配 CLSID。

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包含宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它将 `CComClassFactory` 声明为默认类工厂。 若要重写此默认值，请在类定义中指定 DECLARE_CLASSFACTORY*XXX*宏之一。 例如， [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)宏为类工厂使用指定的类：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

以上类定义指定 `CMyClassFactory` 将用作对象的默认类工厂。 `CMyClassFactory` 必须从 `CComClassFactory` 派生，并重写 `CreateInstance`。

ATL 提供三个声明类工厂的宏：

- [DECLARE_CLASSFACTORY2](#declare_classfactory2)使用通过许可证控制创建的[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，它在多个单元中创建对象。

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)使用构造单个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象的[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)。

##  <a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

将 `cf` 声明为类工厂。

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>参数

*cf*<br/>
中实现类工厂对象的类的名称。

### <a name="remarks"></a>备注

*Cf*参数必须从[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)派生并重写 `CreateInstance` 方法。

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将 `CComClassFactory` 指定为默认类工厂。 但是，通过在对象的类定义中包含 DECLARE_CLASSFACTORY_EX 宏，可以覆盖此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

##  <a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

将[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)声明为类工厂。

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>参数

*lic*<br/>
中一个实现 `VerifyLicenseKey`、`GetLicenseKey`和 `IsLicenseValid`的类。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定为默认类工厂。 但是，通过在对象的类定义中包含 DECLARE_CLASSFACTORY2 宏，可以覆盖此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

##  <a name="ccomclassfactory2_class"></a>CComClassFactory2 类

此类实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口。

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>参数

*license*<br/>
实现以下静态函数的类：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>备注

`CComClassFactory2` 实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口，该接口是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的扩展。 `IClassFactory2` 通过许可证控制对象创建。 在许可计算机上执行的类工厂可以提供运行时许可证密钥。 此许可证密钥允许应用程序在完整的计算机许可证不存在时实例化对象。

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包含宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)声明为默认类工厂。 若要使用 `CComClassFactory2`，请在对象的类定义中指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`，`CComClassFactory2`的模板参数必须实现静态函数 `VerifyLicenseKey`、`GetLicenseKey`和 `IsLicenseValid`。 下面是一个简单许可证类的示例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` 派生自 `CComClassFactory2Base` 和*许可证*。 相反，`CComClassFactory2Base`派生自 `IClassFactory2` 并**CComObjectRootEx\< CComGlobalsThreadModel >** 。

##  <a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

将[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)声明为类工厂。

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定为默认类工厂。 但是，通过在对象的类定义中包含 DECLARE_CLASSFACTORY_AUTO_THREAD 宏，可以覆盖此默认值。

在多个单元中创建对象（在进程外服务器中）时，请将 DECLARE_CLASSFACTORY_AUTO_THREAD 添加到类中。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="ccomclassfactoryautothread_class"></a>CComClassFactoryAutoThread 类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建对象。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>备注

`CComClassFactoryAutoThread` 类似于[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允许在多个单元中创建对象。 若要利用此支持，请从[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)派生 EXE 模块。

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包含宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)声明为默认类工厂。 若要使用 `CComClassFactoryAutoThread`，请在对象的类定义中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

将[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)声明为类工厂。

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>参数

*obj*<br/>
中类对象的名称。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定为默认类工厂。 但是，通过在对象的类定义中包含 DECLARE_CLASSFACTORY_SINGLETON 宏，可以覆盖此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="ccomclassfactorysingleton_class"></a>CComClassFactorySingleton 类

此类派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>参数

*T*<br/>
你的类。

`CComClassFactorySingleton` 派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。 每次调用 `CreateInstance` 方法时，都只会查询此对象的接口指针。

### <a name="remarks"></a>备注

ATL 对象通过从[CComCoClass](../../atl/reference/ccomcoclass-class.md)派生来通常获取类工厂。 此类包含宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它将 `CComClassFactory` 声明为默认类工厂。 若要使用 `CComClassFactorySingleton`，请在对象的类定义中指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

`GetControllingUnknown`声明虚拟函数。

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>备注

如果收到 `GetControllingUnknown` 未定义的编译器错误消息（例如，在 `CComAggregateCreator`中），请将此宏添加到对象。

##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE

指定不能聚合您的对象。

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
中要定义为不可聚合的类对象的名称。

### <a name="remarks"></a>备注

如果尝试聚合到你的对象，DECLARE_NOT_AGGREGATABLE 会导致 `CreateInstance` 返回错误（CLASS_E_NOAGGREGATION）。

默认情况下， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，该宏指定可以聚合对象。 若要重写此默认行为，请在类定义中包括 DECLARE_NOT_AGGREGATABLE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE

指定必须聚合您的对象。

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
中要定义为仅可聚合的类对象的名称。

### <a name="remarks"></a>备注

如果尝试将对象 `CoCreate` 为非聚合对象，DECLARE_ONLY_AGGREGATABLE 会导致错误（E_FAIL）。

默认情况下， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，该宏指定可以聚合对象。 若要重写此默认行为，请在类定义中包括 DECLARE_ONLY_AGGREGATABLE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE

指定在创建对象时创建**CComPolyObject \<** *x* **>** 的实例。

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
中要定义为可聚合或不可聚合的类对象的名称。

### <a name="remarks"></a>备注

在创建过程中，将检查外部 "未知" 的值。 如果为 NULL，则为非聚合对象实现 `IUnknown`。 如果外部未知不为 NULL，则为聚合的对象实现 `IUnknown`。

使用 DECLARE_POLY_AGGREGATABLE 的优点在于，您可以避免在模块中同时使用 `CComAggObject` 和 `CComObject` 来处理聚合和非聚合情况。 单个 `CComPolyObject` 对象处理两种情况。 这意味着在您的模块中只存在一个 vtable 副本和一个函数副本。 如果 vtable 很大，这可能会显著降低模块大小。 但是，如果你的 vtable 较小，则使用 `CComPolyObject` 会导致模块大小稍微大一些，因为它未针对聚合对象或非聚合对象进行优化，因为 `CComAggObject` 和 `CComObject`。

如果使用 ATL 控件向导创建完全控件，则会在对象中自动声明 DECLARE_POLY_AGGREGATABLE 宏。

##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT

保护对象不被删除（在[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)期间）内部聚合对象递增引用计数，然后将计数递减为0。

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

##  <a name="declare_view_status"></a>DECLARE_VIEW_STATUS

将此宏置于 ATL ActiveX 控件的控件类中，以指定容器的 VIEWSTATUS 标志。

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>参数

*statusFlags*<br/>
中VIEWSTATUS 标志。 有关标志列表，请参阅[VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
