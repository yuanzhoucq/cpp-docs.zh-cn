---
title: CAdapt 类
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 23544bc103de0d7b76cd73d403626ba93af6e31a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321630"
---
# <a name="cadapt-class"></a>CAdapt 类

此模板用于包装一些类，这些类将 address-of 运算符重新定义为返回对象地址之外的内容。

## <a name="syntax"></a>语法

```
template <class T>
class CAdapt
```

#### <a name="parameters"></a>参数

*T*<br/>
已适配的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[适应：：适应](#cadapt)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[C 适应：：操作员康斯特 T&](#operator_const_t_amp)|返回对`m_T`的**const**引用。|
|[C 适应：：运算符 T&](#operator_t_amp)|返回对 `m_T` 的引用。|
|[C 适应：：操作员<](#operator_lt)|将已适配类型的对象与 `m_T` 作比较。|
|[适应：：操作员 |](#operator_eq)|将已适配类型的对象分配给 `m_T`。|
|[适应：：操作员 |](#operator_eq_eq)|将已适配类型的对象与 `m_T` 作比较。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C 适应：：m_T](#m_t)|正在适配的数据。|

## <a name="remarks"></a>备注

`CAdapt` 是用于包装类（将 address-of 运算符 (`operator &`) 重新定义为返回对象地址以外的内容）的简单模板。 这样的类的示例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 类，以及编译器 COM 支持类 `_com_ptr_t`。 这些类都重新定义了运算符的地址，以返回其一个数据成员的地址（在`CComBSTR`中为 BSTR，在其他类中为接口指针）。

`CAdapt`主要角色是隐藏*T*类定义的运算符地址，但仍保留已调整类的特征。 `CAdapt`通过持有*T*类型的公共成员`CAdapt`[（m_T），](#m_t)以及定义转换运算符、比较运算符和复制构造函数来实现此角色，以允许将 的专门化视为*T*类的对象。

适配器类 `CAdapt` 很有用，因为某些容器样式类期望能够使用 address-of 运算符获取其包含的对象的地址。 重新定义 address-of 运算符可能使此需求无法得到满足，而且通常会导致编译错误并阻止将非适配类型用于期望它“正常工作”的类。 `CAdapt` 围绕这些问题提供了一种方法。

通常，当你要将 `CAdapt`、`CComBSTR`、`CComPtr` 或 `CComQIPtr` 对象存储在容器样式类中时，你将使用 `_com_ptr_t`。 在大多数情况下，若要支持 C++ 标准，这对于 C++11 标准库容器必需的，但 C++11 标准库容器会自动处理已重载 `operator&()` 的类型。 标准库通过在内部使用[std：：：地址](../../standard-library/memory-functions.md#addressof)来实现此目的，从而获取对象的真实地址。

## <a name="requirements"></a>要求

**标题：** atlcomcli.h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>适应：：适应

构造函数允许默认构造适配器对象、从已调整类型的对象复制或从其他适配器对象复制。

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*rSrc*<br/>
要复制到新构造的适配器对象的类型变量。

*rSrCA*<br/>
其包含数据的适配器对象应复制（或移动）到新构造的适配器对象。

## <a name="cadaptm_t"></a><a name="m_t"></a>C 适应：：m_T

保存要调整的数据。

```
T m_T;
```

### <a name="remarks"></a>备注

此**公共**数据成员可直接或间接地与[操作员 const T&](#operator_const_t_amp)和运算符[T&](#operator_t_amp)进行访问。

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>C 适应：：操作员孔 T&amp;

返回对[m_T](#m_t)成员的**const**引用，允许将适配器对象视为*T*类型的对象。

```
operator const T&() const;
```

### <a name="return-value"></a>返回值

对**const**的`m_T`引用。

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>适应：：运算符 T&amp;

返回对[m_T](#m_t)成员的引用，允许将适配器对象视为*T*类型的对象。

```
operator T&();
```

### <a name="return-value"></a>返回值

对 `m_T` 的引用。

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>C 适应：：操作员&lt;

将适应类型的对象与[m_T](#m_t)进行比较。

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>参数

*rSrc*<br/>
对要比较的对象的引用。

### <a name="return-value"></a>返回值

和*rSrc*`m_T`之间的比较结果。

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>适应：：操作员 |

赋值运算符将参数*rSrc*分配给数据成员[m_T](#m_t)并返回当前适配器对象。

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*rSrc*<br/>
对要复制的已调整类型的对象的引用。

*rSrCA*<br/>
对要移动的对象的引用。

### <a name="return-value"></a>返回值

对当前对象的引用。

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>适应：：操作员 |

将适应类型的对象与[m_T](#m_t)进行比较。

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>参数

*rSrc*<br/>
对要比较的对象的引用。

### <a name="return-value"></a>返回值

*m_T*和*rSrc*比较的结果。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
