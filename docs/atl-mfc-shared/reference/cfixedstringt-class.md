---
title: CFixedStringT 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e6b47642965b73662e63a839796425be855a6523
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879522"
---
# <a name="cfixedstringt-class"></a>CFixedStringT 类
此类表示具有固定的字符缓冲区的字符串对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>参数  
 *StringType*  
 用作固定的字符串的对象的基类，并且可以是任何`CStringT`-基于的类型。 一些示例包括`CString`， `CStringA`，和`CStringW`。  
  
 *t_nChars*  
 存储在缓冲区中的字符数。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|字符串对象的构造函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|将一个新值赋给`CFixedStringT`对象。|  
  
## <a name="remarks"></a>备注  
 此类是基于自定义字符串类的一个示例`CStringT`。 尽管非常类似，但是两个类的实现方式不同。 之间的主要区别`CFixedStringT`和`CStringT`是：  
  
-   初始字符缓冲区分配作为对象的一部分并且其大小*t_nChars*。 这允许`CFixedString`对象以占据连续内存块，以提高性能。 但是，如果的内容`CFixedStringT`对象大小超过指定值*t_nChars*，动态分配的缓冲区。  
  
-   有关字符缓冲区`CFixedStringT`对象始终是相同的长度 ( *t_nChars*)。 缓冲区大小没有限制`CStringT`对象。  
  
-   内存管理器`CFixedStringT`，以便共享的自定义[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)对象在两个或多之间`CFixedStringT`objectsis 不允许。 `CStringT` 对象没有此限制。  
  
 有关详细信息的自定义`CFixedStringT`和字符串对象的内存管理一般情况下，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>要求  
 **标头：** cstringt.h  
  
##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT  
 构造 `CFixedStringT` 对象。  
  
```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```  
  
### <a name="parameters"></a>参数  
 *psz*  
 以 null 结尾的字符串复制到此`CFixedStringT`对象。  
  
 *str*  
 将现有`CFixedStringT`复制到此对象`CFixedStringT`对象。  
  
 *pStringMgr*  
 指向的内存管理器的`CFixedStringT`对象。 有关详细信息`IAtlStringMgr`和内存管理`CFixedStringT`，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
### <a name="remarks"></a>备注  
 因为构造函数将输入的数据复制到新的已分配存储，你应注意异常可能会导致该内存。 请注意这些构造函数的一些充当转换函数。  
  
##  <a name="operator__eq"></a>  CFixedStringT::operator =  
 重新初始化现有`CFixedStringT`对象的新数据。  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>参数  
 *str*  
 以 null 结尾的字符串复制到此`CFixedStringT`对象。  
  
 *psz*  
 将现有`CFixedStringT`复制到此`CFixedStringT`对象。  
  
### <a name="remarks"></a>备注  
 应注意可能会发生异常，每当你使用赋值运算符，因为通常分配新存储，用于保存所生成的内存`CFixedStringT`对象。  
  
## <a name="see-also"></a>请参阅  
 [CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)




