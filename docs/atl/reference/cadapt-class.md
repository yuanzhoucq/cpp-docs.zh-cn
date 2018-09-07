---
title: CAdapt 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
dev_langs:
- C++
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 503ce18d5ffa966f6c216468b487851207313937
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105343"
---
# <a name="cadapt-class"></a>CAdapt 类

此模板用于包装一些类，这些类将 address-of 运算符重新定义为返回对象地址之外的内容。

## <a name="syntax"></a>语法

```
template <class T>  
class CAdapt
```

#### <a name="parameters"></a>参数

*T*  
已适配的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAdapt::CAdapt](#cadapt)|构造函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAdapt::operator const T （& a)](#operator_const_t_amp)|返回**const**引用`m_T`。|
|[CAdapt::operator T （& a)](#operator_t_amp)|返回对 `m_T` 的引用。|
|[CAdapt::operator <](#operator_lt)|将已适配类型的对象与 `m_T` 作比较。|
|[CAdapt::operator =](#operator_eq)|将已适配类型的对象分配给 `m_T`。|
|[CAdapt::operator = =](#operator_eq_eq)|将已适配类型的对象与 `m_T` 作比较。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CAdapt::m_T](#m_t)|正在适配的数据。|

## <a name="remarks"></a>备注

`CAdapt` 是用于包装类（将 address-of 运算符 (`operator &`) 重新定义为返回对象地址以外的内容）的简单模板。 这样的类的示例包括 ATL 的 `CComBSTR`、`CComPtr` 和 `CComQIPtr` 类，以及编译器 COM 支持类 `_com_ptr_t`。 所有这些类重新定义 address-of 运算符以返回一个其数据成员的地址 (的情况下 BSTR `CComBSTR`，并在其他类的情况下的接口指针)。

`CAdapt`主要作用是隐藏由类定义 address-of 运算符*T*，但仍保留已适配的类的特征。 `CAdapt` 通过保留的公共成员，实现了这个作用[m_T](#m_t)，类型的*T*，以及通过定义转换运算符、 比较运算符和复制构造函数，以允许的专用化`CAdapt`为它们被类型的对象视作*T*。

适配器类 `CAdapt` 很有用，因为某些容器样式类期望能够使用 address-of 运算符获取其包含的对象的地址。 重新定义 address-of 运算符可能使此要求无法得到满足，而且通常会导致编译错误并阻止将非适配类型用于期望它“正常工作”的类。 `CAdapt` 围绕这些问题提供了一种方法。

通常，当你要将 `CAdapt`、`CComBSTR`、`CComPtr` 或 `CComQIPtr` 对象存储在容器样式类中时，你将使用 `_com_ptr_t`。 在大多数情况下，若要支持 C++ 标准，这对于 C++11 标准库容器必需的，但 C++11 标准库容器会自动处理已重载 `operator&()` 的类型。 标准库通过在内部使用，从而实现这[std::addressof](../../standard-library/memory-functions.md#addressof)获取对象的真实地址。

## <a name="requirements"></a>要求

**标头：** atlcomcli.h

##  <a name="cadapt"></a>  CAdapt::CAdapt

构造函数允许适配器对象默认情况下构造，复制已适配类型的对象或从另一个适配器对象进行复制。

```
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*rSrc*  
正在适配要复制到新构造的适配器对象类型的变量。

*rSrCA*  
一个适配器对象，其所包含的数据应要复制 （或移动） 到新构造的适配器对象。

##  <a name="m_t"></a>  CAdapt::m_T

保存所应用的数据。

```
T m_T;
```

### <a name="remarks"></a>备注

这**公共**数据成员可以直接或间接使用访问[运算符 const T &](#operator_const_t_amp)并[运算符 T &](#operator_t_amp)。

##  <a name="operator_const_t_amp"></a>  CAdapt::operator const T&amp;

返回**const**引用[m_T](#m_t)成员，这样允许该适配器对象，就好像类型的对象视为*T*。

```  
operator const T&() const;
```

### <a name="return-value"></a>返回值

一个**const**引用`m_T`。

##  <a name="operator_t_amp"></a>  CAdapt::operator T&amp;

返回的引用[m_T](#m_t)成员，这样允许该适配器对象，就好像类型的对象被视为*T*。

```  
operator T&();
```

### <a name="return-value"></a>返回值

对引用`m_T`。

##  <a name="operator_lt"></a>  CAdapt::operator &lt;

将已适配的类型与对象进行比较[m_T](#m_t)。

```
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>参数

*rSrc*  
对要进行比较的对象的引用。

### <a name="return-value"></a>返回值

之间的比较结果`m_T`并*rSrc*。

##  <a name="operator_eq"></a>  CAdapt::operator =

赋值运算符分配参数， *rSrc*，到的数据成员[m_T](#m_t) ，并返回当前的适配器对象。

```
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>参数

*rSrc*  
对要复制已适配类型的对象的引用。

*rSrCA*  
对要移动的对象的引用。

### <a name="return-value"></a>返回值

对当前对象的引用。

##  <a name="operator_eq_eq"></a>  CAdapt::operator = =

将已适配的类型与对象进行比较[m_T](#m_t)。

```
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>参数

*rSrc*  
对要进行比较的对象的引用。

### <a name="return-value"></a>返回值

之间的比较结果*m_T*并*rSrc*。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
