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
ms.openlocfilehash: 2ea8fc8a26642abf593c7f4df3928ff90e66e2b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229995"
---
# <a name="cadapt-class"></a>CAdapt 类

此模板用于包装一些类，这些类将 address-of 运算符重新定义为返回对象地址之外的内容。

## <a name="syntax"></a>语法

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>参数

*T*<br/>
已适配的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAdapt：： operator const T&](#operator_const_t_amp)|返回 **`const`** 对的引用 `m_T` 。|
|[CAdapt：： operator T&](#operator_t_amp)|返回对 `m_T` 的引用。|
|[CAdapt：： operator <](#operator_lt)|将已适配类型的对象与 `m_T` 作比较。|
|[CAdapt：： operator =](#operator_eq)|将已适配类型的对象分配给 `m_T`。|
|[CAdapt：： operator = =](#operator_eq_eq)|将已适配类型的对象与 `m_T` 作比较。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAdapt：： m_T](#m_t)|正在适配的数据。|

## <a name="remarks"></a>备注

`CAdapt` 是用于包装类（将 address-of 运算符 (`operator &`) 重新定义为返回对象地址以外的内容）的简单模板。 这样的类的示例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 类，以及编译器 COM 支持类 `_com_ptr_t`。 这些类都将重定义该地址的运算符，以返回其一个数据成员的地址（对于为，则为一个 BSTR `CComBSTR` ，在其他类的情况下为一个接口指针）。

`CAdapt`的主要作用是隐藏类*T*定义的地址运算符，但仍保留改编类的特征。 `CAdapt`fulfils 此角色的方法是：保存一个[m_T](#m_t)公共成员，m_T *T*，并定义转换运算符、比较运算符和复制构造函数，以允许将的专用化 `CAdapt` 视为类型为*T*的对象。

适配器类 `CAdapt` 很有用，因为某些容器样式类期望能够使用 address-of 运算符获取其包含的对象的地址。 重新定义 address-of 运算符可能使此需求无法得到满足，而且通常会导致编译错误并阻止将非适配类型用于期望它“正常工作”的类。 `CAdapt` 围绕这些问题提供了一种方法。

通常，当你要将 `CAdapt`、`CComBSTR`、`CComPtr` 或 `CComQIPtr` 对象存储在容器样式类中时，你将使用 `_com_ptr_t`。 在大多数情况下，若要支持 C++ 标准，这对于 C++11 标准库容器必需的，但 C++11 标准库容器会自动处理已重载 `operator&()` 的类型。 标准库通过内部使用[std：： addressof](../../standard-library/memory-functions.md#addressof)获取对象的真实地址来实现此操作。

## <a name="requirements"></a>要求

**标头：** atlcomcli。h

## <a name="cadaptcadapt"></a><a name="cadapt"></a>CAdapt::CAdapt

构造函数允许对适配器对象进行默认构造、从改编类型的对象复制或从其他适配器对象复制。

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*.Rsrc*<br/>
要改编为复制到新构造的适配器对象的类型的变量。

*rSrCA*<br/>
应将包含数据的适配器对象复制（或移动）到新构建的适配器对象。

## <a name="cadaptm_t"></a><a name="m_t"></a>CAdapt：： m_T

保存要改编的数据。

```cpp
T m_T;
```

### <a name="remarks"></a>备注

此 **`public`** 数据成员可以直接或间接地通过[Operator const T&](#operator_const_t_amp)和[operator t&](#operator_t_amp)进行访问。

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a>CAdapt：： operator const T&amp;

返回 **`const`** 对[m_T](#m_t)成员的引用，允许将适配器对象视为类型为*T*的对象。

```cpp
operator const T&() const;
```

### <a name="return-value"></a>返回值

对的 **`const`** 引用 `m_T` 。

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a>CAdapt：： operator T&amp;

返回对[m_T](#m_t)成员的引用，允许将适配器对象视为类型为*T*的对象。

```cpp
operator T&();
```

### <a name="return-value"></a>返回值

对 `m_T` 的引用。

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a>CAdapt：： operator&lt;

将改编后的类型的对象与[m_T](#m_t)进行比较。

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>参数

*.Rsrc*<br/>
对要比较的对象的引用。

### <a name="return-value"></a>返回值

与 .Rsrc 之间的比较结果 `m_T` 。 *rSrc*

## <a name="cadaptoperator-"></a><a name="operator_eq"></a>CAdapt：： operator =

赋值运算符将参数 *.rsrc*分配给数据成员[m_T](#m_t)并返回当前适配器对象。

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*.Rsrc*<br/>
对要复制的改编类型的对象的引用。

*rSrCA*<br/>
对要移动的对象的引用。

### <a name="return-value"></a>返回值

对当前对象的引用。

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a>CAdapt：： operator = =

将改编后的类型的对象与[m_T](#m_t)进行比较。

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>参数

*.Rsrc*<br/>
对要比较的对象的引用。

### <a name="return-value"></a>返回值

*M_T*与 *.rsrc*之间的比较结果。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
