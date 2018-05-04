---
title: CComVariant 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2ebef74f6da48d2124d69f002a85c467db73406
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ccomvariant-class"></a>CComVariant 类
此类将包装`VARIANT`提供，该值指示存储的数据类型的成员的类型。  
  
## <a name="syntax"></a>语法  
  
```  
cpp
class CComVariant : public tagVARIANT  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComVariant::CComVariant](#ccomvariant)|构造函数。|  
|[CComVariant:: ~ CComVariant](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComVariant::Attach](#attach)|将附加**VARIANT**到`CComVariant`对象。|  
|[CComVariant::ChangeType](#changetype)|将转换`CComVariant`为新类型的对象。|  
|[CComVariant::Clear](#clear)|清除`CComVariant`对象。|  
|[CComVariant::Copy](#copy)|副本**VARIANT**到`CComVariant`对象。|  
|[CComVariant::CopyTo](#copyto)|内容复制`CComVariant`对象。|  
|[CComVariant::Detach](#detach)|分离基础**VARIANT**从`CComVariant`对象。|  
|[CComVariant::GetSize](#getsize)|返回中的内容的字节数大小`CComVariant`对象。|  
|[CComVariant::ReadFromStream](#readfromstream)|加载**VARIANT**从流。|  
|[CComVariant::SetByRef](#setbyref)|初始化`CComVariant`对象并设置**vt**成员**VT_BYREF**。|  
|[CComVariant::WriteToStream](#writetostream)|将保存基础**VARIANT**到流。|  
  
### <a name="public-operators"></a>公共运算符  
  
|||  
|-|-|  
|[CComVariant::operator <](#operator_lt)|指示是否`CComVariant`对象是否指定小于**VARIANT**。|  
|[CComVariant::operator >](#operator_gt)|指示是否`CComVariant`对象是否大于指定**VARIANT**。|  
|[运算符 ！ =](#operator_neq)|指示是否`CComVariant`对象不等于指定**VARIANT**。|  
|[operator =](#operator_eq)|将值赋给`CComVariant`对象。|  
|[operator ==](#operator_eq_eq)|指示是否`CComVariant`的对象等于指定**VARIANT**。|  
  
## <a name="remarks"></a>备注  
 `CComVariant` 包装`VARIANT and VARIANTARG`类型，其中包含联合和联合中存储的数据类型，该值指示成员。 **VARIANT**s 通常在自动化中使用。  
  
 `CComVariant` 派生自**VARIANT**键入，以便它可以是任何位置使用**VARIANT**可用。 例如，可以使用**V_VT**宏来提取的一种`CComVariant`或可以访问**vt**成员直接就像可以按照与**VARIANT**。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcomcli.h  
  
##  <a name="attach"></a>  CComVariant::Attach  
 安全地清除的当前内容`CComVariant`对象，将复制的内容`pSrc`到此对象，然后设置的变体类型`pSrc`到`VT_EMPTY`。  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>参数  
 `pSrc`  
 [in]指向[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)要附加到对象。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 保存的数据的所有权`pSrc`传输到`CComVariant`对象。  
  
##  <a name="ccomvariant"></a>  CComVariant::CComVariant  
 每个构造函数处理的安全初始化`CComVariant`对象通过调用`VariantInit`Win32 函数或通过设置对象的值和根据传递的参数的类型。  
  
```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```  
  
### <a name="parameters"></a>参数  
 *varSrc*  
 [in]`CComVariant`或`VARIANT`用于初始化`CComVariant`对象。 源变体的内容复制到目标而不进行转换。  
  
 `lpszSrc`  
 [in]用于初始化的字符字符串`CComVariant`对象。 你可以零终止宽 (Unicode) 字符将字符串传递给**LPCOLESTR**版本的构造函数或 ANSI 字符串到`LPCSTR`版本。 在任一情况下字符串转换为 Unicode`BSTR`使用分配**SysAllocString**。 一种`CComVariant`对象将`VT_BSTR`。  
  
 `bSrc`  
 [in]`bool`用于初始化`CComVariant`对象。 `bool`自变量转换为**VARIANT_BOOL**之前存储。 一种`CComVariant`对象将`VT_BOOL`。  
  
 `nSrc`  
 [in]`int`，**字节**，**短**，**长**， **LONGLONG**， **ULONGLONG**， **无符号短**， `unsigned long`，或`unsigned int`用于初始化`CComVariant`对象。 一种`CComVariant`对象将`VT_I4`， `VT_UI1`， `VT_I2`， `VT_I4`， **VT_I8**， **VT_UI8**， **VT_UI2**， **VT_UI4**，或**VT_UI4**分别。  
  
 `vtSrc`  
 [in]该变量的类型。 第一个参数时`int`，有效类型是`VT_I4`和**VT_INT**。 第一个参数时**长**，有效类型是`VT_I4`和`VT_ERROR`。 第一个参数时**double**，有效类型是`VT_R8`和`VT_DATE`。 第一个参数时`unsigned int`，有效类型是**VT_UI4**和**VT_UINT**。  
  
 `fltSrc`  
 [in]**Float**用于初始化`CComVariant`对象。 一种`CComVariant`对象将`VT_R4`。  
  
 `dblSrc`  
 [in]**Double**用于初始化`CComVariant`对象。 一种`CComVariant`对象将`VT_R8`。  
  
 `cySrc`  
 [in]**CY**用于初始化`CComVariant`对象。 一种`CComVariant`对象将`VT_CY`。  
  
 `pSrc`  
 [in]`IDispatch`或**IUnknown**指针用于初始化`CComVariant`对象。 `AddRef` 将在接口指针上调用。 一种`CComVariant`对象将**VT_DISPATCH**或**VT_UNKNOWN**分别。  
  
 或者， **SAFERRAY**指针用于初始化`CComVariant`对象。 一份**SAFEARRAY**存储在`CComVariant`对象。 一种`CComVariant`对象将是原始类型的组合**SAFEARRAY**和**VT_ARRAY**。  
  
 `cSrc`  
 [in]`char`用于初始化`CComVariant`对象。 一种`CComVariant`对象将**VT_I1**。  
  
 `bstrSrc`  
 [in]BSTR 用于初始化`CComVariant`对象。 一种`CComVariant`对象将`VT_BSTR`。  
  
### <a name="remarks"></a>备注  
 析构函数通过调用管理清理[CComVariant::Clear](#clear)。  
  
##  <a name="dtor"></a>  CComVariant:: ~ CComVariant  
 析构函数。  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>备注  
 此方法通过调用管理清理[CComVariant::Clear](#clear)。  
  
##  <a name="changetype"></a>  CComVariant::ChangeType  
 将转换`CComVariant`为新类型的对象。  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `vtNew`  
 [in]新类型`CComVariant`对象。  
  
 `pSrc`  
 [in]指向的指针`VARIANT`其值将转换为新的类型。 默认值是**NULL**，这意味着`CComVariant`将就地转换对象。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 如果您传递一个值`pSrc`，`ChangeType`将使用此**VARIANT**作为转换的源。 否则为`CComVariant`对象将为源。  
  
##  <a name="clear"></a>  CComVariant::Clear  
 清除`CComVariant`对象通过调用`VariantClear`Win32 函数。  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 析构函数自动调用**清除**。  
  
##  <a name="copy"></a>  CComVariant::Copy  
 释放`CComVariant`对象，然后将其分配一份指定**VARIANT**。  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>参数  
 `pSrc`  
 [in]指向的指针[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)要复制。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="copyto"></a>  CComVariant::CopyTo  
 内容复制`CComVariant`对象。  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>参数  
 *pstrDest*  
 指向`BSTR`，将收到的内容的副本`CComVariant`对象。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 **CComVariant**对象的类型必须为`VT_BSTR`。  
  
##  <a name="detach"></a>  CComVariant::Detach  
 分离基础**VARIANT**从`CComVariant`对象，并将该对象的类型设置为`VT_EMPTY`。  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>参数  
 `pDest`  
 [out]返回基础`VARIANT`对象值。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 请注意的内容`VARIANT`所引用的`pDest`自动将在所赋的值和调用类型之前清除**CComVariant**对象。  
  
##  <a name="getsize"></a>  CComVariant::GetSize  
 简单固定大小`VARIANT`s，此方法返回`sizeof`加号的基础数据类型`sizeof(VARTYPE)`。  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>返回值  
 以字节为单位的当前内容的大小`CComVariant`对象。  
  
### <a name="remarks"></a>备注  
 如果`VARIANT`包含的接口指针，`GetSize`查询`IPersistStream`或`IPersistStreamInit`。 如果成功，，则返回值是个返回的值的低 32 位`GetSizeMax`加上`sizeof``CLSID`和`sizeof(VARTYPE)`。 如果接口指针是`NULL`，`GetSize`返回`sizeof``CLSID`加上`sizeof(VARTYPE)`。 如果总大小大于`ULONG_MAX`，`GetSize`返回`sizeof(VARTYPE)`指示错误。  
  
 在所有其他情况下，临时`VARIANT`类型的`VT_BSTR`强制从当前`VARIANT`。 此长度`BSTR`计算为字符串的长度加上其自身的字符串的长度的大小加上加号 null 字符的大小`sizeof(VARTYPE)`。 如果`VARIANT`不能强制转换为`VARIANT`类型的`VT_BSTR`，`GetSize`返回`sizeof(VARTYPE)`。  
  
 此方法返回的大小匹配的使用的字节数[CComVariant::WriteToStream](#writetostream)在成功的情况下。  
  
##  <a name="operator_eq"></a>  CComVariant::operator =  
 将分配一个值，并相应类型设置为`CComVariant`对象。  
  
```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```  
  
### <a name="parameters"></a>参数  
 *varSrc*  
 [in]`CComVariant`或[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)要分配给`CComVariant`对象。 源变体的内容复制到目标而不进行转换。  
  
 `bstrSrc`  
 [in]要分配给的 BSTR`CComVariant`对象。 一种`CComVariant`对象将`VT_BSTR`。  
  
 `lpszSrc`  
 [in]要分配给字符串`CComVariant`对象。 你可以零终止宽 (Unicode) 字符将字符串传递给**LPCOLESTR**版本运算符或 ANSI 字符串到`LPCSTR`版本。 在任一情况下，字符串转换为 Unicode`BSTR`使用分配**SysAllocString**。 一种`CComVariant`对象将`VT_BSTR`。  
  
 `bSrc`  
 [in]`bool`要分配给`CComVariant`对象。 `bool`自变量转换为**VARIANT_BOOL**之前存储。 一种`CComVariant`对象将`VT_BOOL`。  
  
 `nSrc`  
 [in]`int`，**字节**，**短**，**长**， **LONGLONG**， **ULONGLONG**， **无符号短**， `unsigned long`，或`unsigned int`要分配给`CComVariant`对象。 一种`CComVariant`对象将`VT_I4`， `VT_UI1`， `VT_I2`， `VT_I4`， **VT_I8**， **VT_UI8**， **VT_UI2**， **VT_UI4**，或**VT_UI4**分别。  
  
 `fltSrc`  
 [in]**Float**要分配给`CComVariant`对象。 一种`CComVariant`对象将`VT_R4`。  
  
 `dblSrc`  
 [in]**Double**要分配给`CComVariant`对象。 一种`CComVariant`对象将`VT_R8`。  
  
 `cySrc`  
 [in]**CY**要分配给`CComVariant`对象。 一种`CComVariant`对象将`VT_CY`。  
  
 `pSrc`  
 [in]`IDispatch`或**IUnknown**指针分配给`CComVariant`对象。 `AddRef` 将在接口指针上调用。 一种`CComVariant`对象将**VT_DISPATCH**或**VT_UNKNOWN**分别。  
  
 或者， **SAFEARRAY**指针分配给`CComVariant`对象。 一份**SAFEARRAY**存储在`CComVariant`对象。 一种`CComVariant`对象将是原始类型的组合**SAFEARRAY**和**VT_ARRAY**。  
  
 `cSrc`  
 [in]要分配给 char`CComVariant`对象。 一种`CComVariant`对象将**VT_I1**。  
  
##  <a name="operator_eq_eq"></a>  CComVariant::operator = =  
 指示是否`CComVariant`的对象等于指定**VARIANT**。  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>备注  
 返回**true**如果值和类型*varSrc*等于的值和类型，分别的`CComVariant`对象。 否则为**false**。 操作员使用用户的默认区域设置执行比较。  
  
 运算符将仅变体类型的值进行比较。 它将比较字符串、 整数和浮点点，但不是数组或记录。  
  
##  <a name="operator_neq"></a>  CComVariant::operator ！ =  
 指示是否`CComVariant`对象不等于指定**VARIANT**。  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>备注  
 返回**true**如果值或类型的*varSrc*是否不等于值或键入，分别的`CComVariant`对象。 否则为**false**。 操作员使用用户的默认区域设置执行比较。  
  
 运算符将仅变体类型的值进行比较。 它将比较字符串、 整数和浮点点，但不是数组或记录。  
  
##  <a name="operator_lt"></a>  CComVariant::operator &lt;  
 指示是否`CComVariant`对象是否指定小于**VARIANT**。  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>备注  
 返回**true**如果的值`CComVariant`对象是小于的值*varSrc*。 否则为**false**。 操作员使用用户的默认区域设置执行比较。  
  
##  <a name="operator_gt"></a>  CComVariant::operator &gt;  
 指示是否`CComVariant`对象是否大于指定**VARIANT**。  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>备注  
 返回**true**如果的值`CComVariant`对象是否大于值*varSrc*。 否则为**false**。 操作员使用用户的默认区域设置执行比较。  
  
##  <a name="readfromstream"></a>  CComVariant::ReadFromStream  
 设置基础**VARIANT**到**VARIANT**包含在指定的流。  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]指向的指针[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)上包含数据的流的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 **ReadToStream**需要的以前调用[WriteToStream](#writetostream)。  
  
##  <a name="setbyref"></a>  CComVariant::SetByRef  
 初始化`CComVariant`对象并设置**vt**成员**VT_BYREF**。  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>参数  
 `T`  
 一种**VARIANT**，例如， `BSTR`， `int`，或`char`。  
  
 *PT*  
 用于初始化的指针`CComVariant`对象。  
  
### <a name="remarks"></a>备注  
 `SetByRef` 是一个函数模板，初始化`CComVariant`对象与指针*pT*和设置**vt**成员**VT_BYREF**。 例如：  
  
 [!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>  CComVariant::WriteToStream  
 将保存基础**VARIANT**到流。  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]指向的指针[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)流上的接口。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)