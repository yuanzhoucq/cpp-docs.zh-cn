---
title: "CStrBufT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CStrBufT<TCharType>
- ATL.CStrBufT
- CStrBufT
- ATL::CStrBufT
- ATL.CStrBufT<TCharType>
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
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
ms.openlocfilehash: 2eb551d2db029de88aa9c1b456c44609b7fc0922
ms.lasthandoff: 02/24/2017

---
# <a name="cstrbuft-class"></a>CStrBufT 类
此类提供的自动资源清理`GetBuffer`和`ReleaseBuffer`调用在现有`CStringT`对象。  
  
## <a name="syntax"></a>语法  
  
```
template<typename TCharType>
class CStrBufT
```  
  
#### <a name="parameters"></a>参数  
 *TCharType*  
 字符类型`CStrBufT`类。 可以是以下各项之一：  
  
- `char`（针对 ANSI 字符串）  
  
- `wchar_t`（对于 Unicode 字符串）  
  
- **TCHAR** （针对 ANSI 和 Unicode 字符串）  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`PCXSTR`|指向常量字符串的指针。|  
|`PXSTR`|指向字符串的指针。|  
|`StringType`|通过此类模板的专用化操作其缓冲区字符串类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft)|字符串缓冲区对象的构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CStrBufT::SetLength](#setlength)|设置关联的字符串对象的字符的缓冲区长度。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|检索**const**指向字符缓冲区关联的字符串对象的指针。|  
|[CStrBufT::operator PXSTR](#operator_pxstr)|检索指向字符缓冲区关联的字符串对象的指针。|  
  
### <a name="public-constants"></a>公共常量  
  
|名称|说明|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#auto_length)|自动确定字符串中发布的新长度。|  
|[CStrBufT::SET_LENGTH](#set_length)|在 GetBuffer 时设置的字符串对象的长度|  
  
## <a name="remarks"></a>备注  
 此类可作为一个包装类对的调用替换为[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)，或[GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)和`ReleaseBuffer`。  
  
 主要设计为帮助器类，`CStrBufT`可以方便地为开发人员使用的字符缓冲区的字符串对象而无需担心如何或何时调用`ReleaseBuffer`。 这可能是因为包装对象超出范围自然会发生异常或多个现有的代码路径;导致其析构函数释放字符串资源。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsimpstr.h  
  
##  <a name="a-nameautolengtha--cstrbuftautolength"></a><a name="auto_length"></a>CStrBufT::AUTO_LENGTH  
 自动确定字符串中发布的新长度。  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### <a name="remarks"></a>备注  
 自动确定字符串中发布的新长度。 字符串必须是以 null 结尾。  
  
##  <a name="a-namecstrbufta--cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT  
 构造一个缓冲对象。  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `str`  
 与该缓冲区关联的字符串对象。 通常，开发人员将使用的预定义的 typedef **CStrBuf** ( **TCHAR** variant 类型的值)， **CStrBufA** ( `char` variant 类型的值) 和**CStrBufW** ( `wchar_t` variant 类型的值)。  
  
 *nMinLength*  
 字符缓冲区的最小长度。  
  
 `dwFlags`  
 确定是否自动确定字符串长度。 可以是以下各项之一：  
  
- **AUTO_LENGTH**字符串长度将自动确定何时[CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)调用。 字符串必须是以 null 结尾。 默认值。  
  
- **SET_LENGTH**时设置字符串的长度[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)调用。  
  
### <a name="remarks"></a>备注  
 创建关联的字符串对象的字符串缓冲区。 在构造期间[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)调用。  
  
 请注意，复制构造函数是`private`。  
  
##  <a name="a-nameoperatorpcxstra--cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::operator PCXSTR  
 直接访问存储在关联的字符串对象用作 C 样式字符串的字符。  
  
```  
operator PCXSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 指向字符串的数据的字符指针。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回指向字符串对象的字符缓冲区的指针。 字符串对象的内容不能更改与此指针。  
  
##  <a name="a-nameoperatorpxstra--cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::operator PXSTR  
 直接访问存储在关联的字符串对象用作 C 样式字符串的字符。  
  
```
operator PXSTR() throw();
```  
  
### <a name="return-value"></a>返回值  
 指向字符串的数据的字符指针。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回指向字符串对象的字符缓冲区的指针。 开发人员可能会更改与此指针的字符串对象的内容。  
  
##  <a name="a-namepcxstra--cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR  
 指向常量字符串的指针。  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="a-namepxstra--cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR  
 指向字符串的指针。  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="a-namesetlengtha--cstrbuftsetlength"></a><a name="set_length"></a>CStrBufT::SET_LENGTH  
 处的字符串对象的长度设置`GetBuffer`时间。  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### <a name="remarks"></a>备注  
 在 GetBuffer 时设置的字符串对象的长度。  
  
 确定如果[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)构造字符串的缓冲区对象时调用。  
  
##  <a name="a-namesetlengtha--cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::SetLength  
 设置字符缓冲区的长度。  
  
```
void SetLength(int nLength);
```  
  
### <a name="parameters"></a>参数  
 `nLength`  
 新的字符串对象的字符缓冲区的长度。  
  
> [!NOTE]
>  必须小于或等于指定的构造函数中的最小缓冲区长度`CStrBufT`。  
  
### <a name="remarks"></a>备注  
 调用此函数可设置所表示的缓冲区对象的字符串的长度。  
  
##  <a name="a-namestringtypea--cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::StringType  
 通过此类模板的专用化操作其缓冲区字符串类型。  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### <a name="remarks"></a>备注  
 **TCharType**是用来特殊化类模板的字符类型。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)



