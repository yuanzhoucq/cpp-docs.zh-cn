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
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319341"
---
# <a name="aggregation-and-class-factory-macros"></a>聚合和类工厂宏

这些宏提供了控制聚合和声明类工厂的方法。

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|声明可以聚合对象（默认值）。|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|声明类工厂为[CComClassFactory，ATL](../../atl/reference/ccomclassfactory-class.md)默认类工厂。|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|将类工厂对象声明为类工厂。|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|声明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)为类工厂。|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|声明[CComClass 工厂自动线程](../../atl/reference/ccomclassfactoryautothread-class.md)为类工厂。|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|宣布[CComClass工厂单顿](../../atl/reference/ccomclassfactorysingleton-class.md)为类工厂。|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|声明虚拟`GetControllingUnknown`函数。|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|声明无法聚合对象。|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|声明必须聚合对象。|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|检查外部未知值，并酌情声明对象可聚合或不可聚合。|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|在内部对象构造期间保护外部对象不删除。|
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定容器的"视图状态"标志。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

指定可以聚合对象。

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]要定义为聚合的类的名称。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含此宏以指定默认聚合模型。 要重写此默认值，请在类定义中指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)为类工厂。

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)使用此宏声明对象的默认类工厂。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>CComClass 工厂类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>备注

`CComClassFactory`实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，其中包含用于创建特定 CLSID 对象的方法，以及将类工厂锁定在内存中，以便更快地创建新对象。 `IClassFactory`必须针对在系统注册表中注册并为其分配 CLSID 的每个类实现。

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它`CComClassFactory`声明为默认类工厂。 要重写此默认值，请在类定义中指定DECLARE_CLASSFACTORY*XXX*宏之一。 例如[，DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)宏对类工厂使用指定的类：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

上面的类定义指定`CMyClassFactory`将用作对象的默认类工厂。 `CMyClassFactory`必须派生并`CComClassFactory`覆盖`CreateInstance`。

ATL 提供了声明类工厂的其他三个宏：

- [DECLARE_CLASSFACTORY2](#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，它控制通过许可证创建的。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，它可在多个单元中创建对象。

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)使用[CComClassFactory 单一项](../../atl/reference/ccomclassfactorysingleton-class.md)，它构造单个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

声明`cf`为类工厂。

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>参数

*Cf*<br/>
[在]实现类工厂对象的类的名称。

### <a name="remarks"></a>备注

*cf*参数必须派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)并`CreateInstance`重写该方法。

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏`CComClassFactory`指定为默认类工厂。 但是，通过将DECLARE_CLASSFACTORY_EX宏包括在对象的类定义中，可以覆盖此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

声明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)为类工厂。

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>参数

*虱子*<br/>
[在]实现`VerifyLicenseKey``GetLicenseKey`的类 ，`IsLicenseValid`和 。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定为默认类工厂。 但是，通过将DECLARE_CLASSFACTORY2宏包括在对象的类定义中，可以覆盖此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>CComClassFactory2 类

此类实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口。

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>参数

*许可证*<br/>
实现以下静态函数的类：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>备注

`CComClassFactory2`实现[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)接口，这是[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)的扩展。 `IClassFactory2`通过许可证控制对象创建。 在许可计算机上执行的类工厂可以提供运行时许可证密钥。 此许可证密钥允许应用程序在不存在完整的计算机许可证时实例化对象。

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)为默认类工厂。 要使用`CComClassFactory2`，请在对象的类定义中指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`的`CComClassFactory2`模板参数必须实现静态函数`VerifyLicenseKey`和`GetLicenseKey``IsLicenseValid`。 下面是一个简单的许可证类的示例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`派生自和`CComClassFactory2Base`*许可证*。 `CComClassFactory2Base`，反过来，派生自`IClassFactory2`和**CComObjectRootEx\< CComGlobalsThread模型>**。

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

声明[CComClass 工厂自动线程](../../atl/reference/ccomclassfactoryautothread-class.md)为类工厂。

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定为默认类工厂。 但是，通过将DECLARE_CLASSFACTORY_AUTO_THREAD宏包括在对象的类定义中，可以覆盖此默认值。

在多个单元（在 proc 服务器中）创建对象时，将DECLARE_CLASSFACTORY_AUTO_THREAD添加到类中。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>CComclass 工厂自动线程类

此类实现[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>备注

`CComClassFactoryAutoThread`类似于[CComClassFactory，](../../atl/reference/ccomclassfactory-class.md)但允许在多个公寓中创建对象。 要利用此支持，请从[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)派生 EXE 模块。

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)为默认类工厂。 要使用`CComClassFactoryAutoThread`，请在对象的类定义中指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

宣布[CComClass工厂单顿](../../atl/reference/ccomclassfactorysingleton-class.md)为类工厂。

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>参数

obj**<br/>
[在]类对象的名称。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，该宏将[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)指定为默认类工厂。 但是，通过将DECLARE_CLASSFACTORY_SINGLETON宏包括在对象的类定义中，可以覆盖此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>CComClass工厂单顿类

此类派生自[CComClassFactory，](../../atl/reference/ccomclassfactory-class.md)并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>参数

*T*<br/>
你的班级

`CComClassFactorySingleton`派生自[CComClassFactory，](../../atl/reference/ccomclassfactory-class.md)并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造单个对象。 对方法`CreateInstance`的每个调用都只是查询此对象作为接口指针。

### <a name="remarks"></a>备注

ATL 对象通常通过[CComCoClass](../../atl/reference/ccomcoclass-class.md)获得类工厂。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，它`CComClassFactory`声明为默认类工厂。 要使用`CComClassFactorySingleton`，请在对象的类定义中指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

声明虚拟函数`GetControllingUnknown`。

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>备注

如果收到未定义的编译器错误消息`GetControllingUnknown`（例如，在 中`CComAggregateCreator`），则此宏添加到对象。

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

指定无法聚合对象。

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]要定义为不可聚合的类对象的名称。

### <a name="remarks"></a>备注

如果尝试`CreateInstance`聚合到对象上，DECLARE_NOT_AGGREGATABLE会导致返回错误（CLASS_E_NOAGGREGATION）。

默认情况下[，CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，该宏指定可以聚合对象。 要重写此默认行为，请在类定义中包括DECLARE_NOT_AGGREGATABLE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

指定必须聚合对象。

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]要定义为仅聚合的类对象的名称。

### <a name="remarks"></a>备注

如果尝试将对象作为非聚合对象进行`CoCreate`，DECLARE_ONLY_AGGREGATABLE会导致错误（E_FAIL）。

默认情况下[，CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，该宏指定可以聚合对象。 要重写此默认行为，请在类定义中包括DECLARE_ONLY_AGGREGATABLE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

指定在创建对象时创建**CComPolyObject \< ** *x***>** 的实例。

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

** x <br/>
[在]要定义为可聚合或不可聚合的类对象的名称。

### <a name="remarks"></a>备注

在创建期间，将检查外部未知值。 如果为 NULL，`IUnknown`则为非聚合对象实现。 如果外部未知值不是 NULL，`IUnknown`则为聚合对象实现。

使用DECLARE_POLY_AGGREGATABLE的优点是，您避免在模块`CComAggObject``CComObject`中同时处理聚合和非聚合情况。 单个`CComPolyObject`对象处理这两种情况。 这意味着模块中仅存在一个 vtable 副本和一个函数副本。 如果 vtable 很大，这可大幅减小模块大小。 但是，如果 vtable 很小，则`CComPolyObject`使用可能会导致模块大小稍大一些，因为它未针对聚合或非聚合对象进行优化，例如`CComAggObject`和`CComObject`。

如果使用 ATL 控制向导创建完全控件，则DECLARE_POLY_AGGREGATABLE宏将自动在对象中声明。

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

如果（在[Final构造](ccomobjectrootex-class.md#finalconstruct)期间）内部聚合对象递增引用计数，然后将计数缩减为 0，则保护对象不被删除。

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

将此宏放在 ATL ActiveX 控件的控制类中，以将"视点"标志指定到容器。

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>参数

*状态标志*<br/>
[在]视图状态标志。 有关标志列表，请参阅[视图状态](/windows/win32/api/ocidl/ne-ocidl-viewstatus)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
