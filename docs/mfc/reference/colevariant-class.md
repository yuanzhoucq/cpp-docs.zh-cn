---
title: "COleVariant 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
dev_langs:
- C++
helpviewer_keywords:
- Automation, parameter types
- COleVariant class
- VARIANT data type
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 753566adc5fc8e48ad31da52c2bb3f04c9e21727
ms.lasthandoff: 02/24/2017

---
# <a name="colevariant-class"></a>COleVariant 类
封装[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)数据类型。  
  
## <a name="syntax"></a>语法  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleVariant::COleVariant](#colevariant)|构造 `COleVariant` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleVariant::Attach](#attach)|将附加**VARIANT**到`COleVariant`。|  
|[COleVariant::ChangeType](#changetype)|更改此变体类型`COleVariant`对象。|  
|[COleVariant::Clear](#clear)|清除此`COleVariant`对象。|  
|[COleVariant::Detach](#detach)|分离**VARIANT**从`COleVariant`，并返回**VARIANT**。|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|从现有变量数组中检索一个字节数组。|  
|[COleVariant::SetString](#setstring)|为特定类型，通常 ANSI 设置的字符串。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|将转换`COleVariant`值到`LPCVARIANT`。|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|将转换`COleVariant`对象插入`LPVARIANT`。|  
|[COleVariant::operator =](#operator_eq)|副本`COleVariant`值。|  
|[COleVariant::operator = =](#operator_eq_eq)|比较两个`COleVariant`值。|  
|[COleVariant::operator &lt; &lt;，&gt;&gt;](#operator_lt_lt__gt_gt)|输出`COleVariant`值赋给`CArchive`或`CDumpContext`和输入`COleVariant`对象从`CArchive`。|  
  
## <a name="remarks"></a>备注  
 OLE 自动化中使用此数据类型。 具体而言， [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b)结构包含指向数组的指针**VARIANT**结构。 一个**DISPPARAMS**结构用于将参数传递给[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
> [!NOTE]
>  此类派生自**VARIANT**结构。 这意味着您可以通过`COleVariant`参数，它将调用中**VARIANT**的数据成员**VARIANT**结构不是可访问的数据成员的`COleVariant`。  
  
 MFC 类的两个相关[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)封装的 variant 数据类型**货币**( `VT_CY`) 和**日期**( `VT_DATE`)。 `COleVariant`类在 DAO 类中广泛使用; 请参阅此类，这些类的典型的用法示例[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。  
  
 有关详细信息，请参阅[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)，[货币](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e)， [DISPPARAMS](http://msdn.microsoft.com/en-us/a16e5a21-766e-4287-b039-13429aa78f8b)，和[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息`COleVariant`类和在 OLE 自动化中的使用它，请参见"传递的参数在 OLE 自动化"文章中[自动化](../../mfc/automation.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="attach"></a>COleVariant::Attach  
 调用此函数可将附加给定[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)对象与当前`COleVariant`对象。  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>参数  
 *varSrc*  
 现有**VARIANT**对象附加到当前`COleVariant`对象。  
  
### <a name="remarks"></a>备注  
 此函数设置[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)的*varSrc*到`VT_EMPTY`。  
  
 有关详细信息，请参阅[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)和[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="colevariant"></a>COleVariant::COleVariant  
 构造 `COleVariant` 对象。  
  
```  
COleVariant(); 
COleVariant(const VARIANT& varSrc); 
COleVariant(const COleVariant& varSrc); 
COleVariant(LPCVARIANT pSrc); 
COleVariant(LPCTSTR lpszSrc); 
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc); 
COleVariant(CString& strSrc); 
COleVariant(BYTE nSrc); 
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2); 
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4); 
COleVariant(const COleCurrency& curSrc); 
COleVariant(float fltSrc); 
COleVariant(double dblSrc); 
COleVariant(const COleDateTime& timeSrc); 
COleVariant(const CByteArray& arrSrc); 
COleVariant(const CLongBinary& lbSrc); 
COleVariant(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>参数  
 *varSrc*  
 现有`COleVariant`或**VARIANT**对象复制到新`COleVariant`对象。  
  
 `pSrc`  
 一个指向**VARIANT**对象，它将被复制到新`COleVariant`对象。  
  
 `lpszSrc`  
 以 null 结尾的字符串复制到新`COleVariant`对象。  
  
 `vtSrc`  
 `VARTYPE`新`COleVariant`对象。  
  
 `strSrc`  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象复制到新`COleVariant`对象。  
  
 `nSrc`, `lSrc`  
 要复制到新的 `COleVariant` 对象中的数值。  
  
 `vtSrc`  
 `VARTYPE`新`COleVariant`对象。  
  
 `curSrc`  
 一个[COleCurrency](../../mfc/reference/colecurrency-class.md)对象复制到新`COleVariant`对象。  
  
 `fltSrc`, `dblSrc`  
 要复制到新的 `COleVariant` 对象中的数值。  
  
 `timeSrc`  
 一个[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象复制到新`COleVariant`对象。  
  
 `arrSrc`  
 一个[CByteArray](../../mfc/reference/cbytearray-class.md)对象复制到新`COleVariant`对象。  
  
 `lbSrc`  
 一个[CLongBinary](../../mfc/reference/clongbinary-class.md)对象复制到新`COleVariant`对象。  
  
 `pidl`  
 一个指向[ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321)要复制到新结构`COleVariant`对象。  
  
### <a name="remarks"></a>备注  
 所有这些构造函数创建新`COleVariant`对象初始化为指定的值。 遵循这些构造函数的简要说明。  
  
- **COleVariant （)**创建一个空`COleVariant`对象， `VT_EMPTY`。  
  
- **COleVariant (** *varSrc* **)**将复制的现有**VARIANT**或`COleVariant`对象。 变体类型将保留。  
  
- **COleVariant (** `pSrc` **)**将复制的现有**VARIANT**或`COleVariant`对象。 变体类型将保留。  
  
- **COleVariant (** `lpszSrc` **)**将一个字符串复制到新的对象， `VT_BSTR` (UNICODE)。  
  
- **COleVariant (** `lpszSrc` **，** `vtSrc` **)**将一个字符串复制到新的对象。 该参数`vtSrc`必须`VT_BSTR`(UNICODE) 或`VT_BSTRT`(ANSI)。  
  
- **COleVariant (** `strSrc` **)**将一个字符串复制到新的对象， **VT_BSTR** (UNICODE)。  
  
- **COleVariant (** `nSrc` **)**的 8 位整数，将复制到新的对象， `VT_UI1`。  
  
- **COleVariant (** `nSrc` **，** `vtSrc` **)**将 16 位整数 （或布尔值） 复制到新的对象。 该参数`vtSrc`必须`VT_I2`或`VT_BOOL`。  
  
- **COleVariant (** `lSrc` **，** `vtSrc` **)**复制 32 位整数 (或`SCODE`值) 到新的对象。 该参数`vtSrc`必须`VT_I4`， `VT_ERROR`，或`VT_BOOL`。  
  
- **COleVariant (** `curSrc` **)**副本**COleCurrency**值转换为新的对象， `VT_CY`。  
  
- **COleVariant (** `fltSrc` **)**将 32 位浮点值复制到新的对象， `VT_R4`。  
  
- **COleVariant (** `dblSrc` **)**将 64 位浮点值复制到新的对象， `VT_R8`。  
  
- **COleVariant (** `timeSrc` **)**副本`COleDateTime`值转换为新的对象， `VT_DATE`。  
  
- **COleVariant (** `arrSrc` **)**副本`CByteArray`对象插入新对象， `VT_EMPTY`。  
  
- **COleVariant (** `lbSrc` **)**副本`CLongBinary`对象插入新对象， `VT_EMPTY`。  
  
 有关详细信息`SCODE`，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="changetype"></a>COleVariant::ChangeType  
 在此变量值的转换的类型`COleVariant`对象。  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `vartype`  
 [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)此`COleVariant`对象。  
  
 `pSrc`  
 一个指向[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)要转换对象。 如果此值为**NULL**，则此`COleVariant`对象用作转换的源。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)， [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)，和[VariantChangeType](http://msdn.microsoft.com/en-us/48a51e32-95d7-4eeb-8106-f5043ffa2fd1)中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="clear"></a>COleVariant::Clear  
 清除**VARIANT**。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
 这会将设置**VARTYPE**为此对象传递给`VT_EMPTY`。 `COleVariant`析构函数将调用此函数。  
  
 有关详细信息，请参阅`VARIANT`， `VARTYPE`，和`VariantClear`中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="detach"></a>COleVariant::Detach  
 分离基础[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)从此对象`COleVariant`对象。  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>备注  
 此函数设置[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)此`COleVariant`对象传递给`VT_EMPTY`。  
  
> [!NOTE]
>  之后调用**分离**，它是由调用方负责调用**VariantClear**所产生**VARIANT**结构。  
  
 有关详细信息，请参阅[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)， [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)，和[VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray  
 从现有变量数组中检索一个字节数组  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>参数  
 `bytes`  
 对现有的引用[CByteArray](../../mfc/reference/cbytearray-class.md)对象。  
  
##  <a name="operator_lpcvariant"></a>COleVariant::operator LPCVARIANT  
 此强制转换运算符将返回`VARIANT`从此复制其值的结构`COleVariant`对象。  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="operator_lpvariant"></a>COleVariant::operator LPVARIANT  
 调用此强制转换运算符来访问基础`VARIANT`此结构`COleVariant`对象。  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>备注  
  
> [!CAUTION]
>  更改中的值**VARIANT**访问此函数返回的指针的结构将此值更改`COleVariant`对象。  
  
##  <a name="operator_eq"></a>COleVariant::operator =  
 这些重载的赋值运算符将源值复制到此`COleVariant`对象。  
  
```  
const COleVariant& operator=(const VARIANT& varSrc); 
const COleVariant& operator=(LPCVARIANT pSrc); 
const COleVariant& operator=(const COleVariant& varSrc); 
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc); 
const COleVariant& operator=(BYTE nSrc); 
const COleVariant& operator=(short nSrc); 
const COleVariant& operator=(long lSrc); 
const COleVariant& operator=(const COleCurrency& curSrc); 
const COleVariant& operator=(float fltSrc); 
const COleVariant& operator=(double dblSrc); 
const COleVariant& operator=(const COleDateTime& dateSrc); 
const COleVariant& operator=(const CByteArray& arrSrc); 
const COleVariant& operator=(const CLongBinary& lbSrc);
```  
  
### <a name="remarks"></a>备注  
 每个运算符的简要说明如下所示︰  
  
- **运算符 = (** *varSrc***)**将复制的现有**VARIANT**或`COleVariant`到此对象的对象。  
  
- **运算符 = (** `pSrc` **)**副本**VARIANT**对象访问`pSrc`到此对象。  
  
- **运算符 = (** `lpszSrc` **)**将以 null 结尾的字符串复制到此对象并设置**VARTYPE**到`VT_BSTR`。  
  
- **运算符 = (** `strSrc` **)**副本[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象插入此对象并设置**VARTYPE**到`VT_BSTR`。  
  
- **运算符 = (** `nSrc` **)**将一个 8 位或 16 位整数值复制到此对象。 如果`nSrc`是 8 位值， **VARTYPE**这将设置为`VT_UI1`。 如果`nSrc`是 16 位值和**VARTYPE**这是`VT_BOOL`，它是保留; 否则为设置为`VT_I2`。  
  
- **运算符 = (** `lSrc` **)**将 32 位整数值复制到此对象。 如果**VARTYPE**这是`VT_ERROR`，它是保留; 否则为设置为`VT_I4`。  
  
- **运算符 = (** `curSrc` **)**副本[COleCurrency](../../mfc/reference/colecurrency-class.md)对象插入此对象并设置**VARTYPE**到`VT_CY`。  
  
- **运算符 = (** `fltSrc` **)**将 32 位浮点值复制到此对象并设置**VARTYPE**到`VT_R4`。  
  
- **运算符 = (** `dblSrc` **)**将 64 位浮点值复制到此对象并设置**VARTYPE**到`VT_R8`。  
  
- **运算符 = (** `dateSrc` **)**副本[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象插入此对象并设置**VARTYPE**到`VT_DATE`。  
  
- **运算符 = (** `arrSrc` **)**副本[CByteArray](../../mfc/reference/cbytearray-class.md)对象插入这`COleVariant`对象。  
  
- **运算符 = (** `lbSrc` **)**副本[CLongBinary](../../mfc/reference/clongbinary-class.md)对象插入这`COleVariant`对象。  
  
 有关详细信息，请参阅[VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118)和[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)中的条目[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="operator_eq_eq"></a>COleVariant::operator = =  
 此运算符比较两个变量的值并返回非零，如果它们相等;否则为 0。  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>COleVariant::operator &lt; &lt;，&gt;&gt;  
 输出`COleVariant`值赋给`CArchive`或**CdumpContext**和输入`COleVariant`对象从`CArchive`。  
  
```  
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,  
    OleVariant varSrc);
 
friend CArchive& AFXAPI operator<<(
    CArchive& ar,  
    COleVariant varSrc);
 
friend CArchive& AFXAPI operator>>(
    CArchive& ar,  
    COleVariant& varSrc);
```  
  
### <a name="remarks"></a>备注  
 `COleVariant`插入 ( ** < \< **) 运算符支持诊断转储并存储到存档中。 提取 ( ** >> **) 运算符支持从存档加载。  
  
##  <a name="setstring"></a>COleVariant::SetString  
 设置为特定类型的字符串。  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>参数  
 `lpszSrc`  
 以 null 结尾的字符串复制到新`COleVariant`对象。  
  
 *VtSrc*  
 **VARTYPE**新`COleVariant`对象。  
  
### <a name="remarks"></a>备注  
 该参数`vtSrc`必须`VT_BSTR`(UNICODE) 或`VT_BSTRT`(ANSI)。 `SetString`通常用于设置为 ANSI 字符串，因为默认值为[COleVariant::COleVariant](#colevariant)构造函数包含一个字符串或字符串的指针参数，但不**VARTYPE**是 unicode 格式。  
  
 在非 UNICODE 版本的 DAO 记录集期望为 ANSI 字符串。 因此，用于 DAO 函数使用`COleVariant`对象，如果不在创建 UNICODE 记录集，则必须使用**COleVariant::COleVariant (** `lpszSrc` **，** `vtSrc` **)**形式的构造函数与`vtSrc`设置为`VT_BSTRT`(ANSI) 或使用`SetString`与`vtSrc`设置为`VT_BSTRT`为了生成 ANSI 字符串。 例如，`CDaoRecordset`函数[CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)使用`COleVariant`对象作为参数。 如果 DAO 记录集不是 unicode 格式，这些对象必须是 ANSI。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)




