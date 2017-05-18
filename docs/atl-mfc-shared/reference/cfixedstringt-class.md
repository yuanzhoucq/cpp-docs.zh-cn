---
title: "CFixedStringT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f357a70a728b388c3b5d3d26ac4efd0d4c84434a
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cfixedstringt-class"></a>CFixedStringT 类
此类表示具有固定的字符缓冲区的字符串对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>参数  
 `StringType`  
 作为基类用于固定的字符串对象，可以是任何`CStringT`的基类型。 一些示例包括`CString`， `CStringA`，和`CStringW`。  
  
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
 此类是基于自定义字符串类的一个示例`CStringT`。 尽管非常类似，但是两个类的实现方式不同。 之间的主要差异`CFixedStringT`和`CStringT`是︰  
  
-   初始字符缓冲区分配对象的一部分，它具有大小*t_nChars*。 这允许**CFixedString**对象以占据连续内存块，以提高性能。 但是，如果内容`CFixedStringT`对象大小超过指定值*t_nChars*，动态分配的缓冲区。  
  
-   对于字符缓冲区`CFixedStringT`对象始终是相同的长度 ( *t_nChars*)。 上的缓冲区大小没有限制`CStringT`对象。  
  
-   内存管理器为`CFixedStringT`已自定义，以便共享[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)对象的两个或多`CFixedStringT`objectsis 不允许使用。 `CStringT`对象不具有这种限制。  
  
 有关详细信息的自定义`CFixedStringT`和字符串对象的内存管理一般情况下，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>要求  
 **标头︰** cstringt.h  
  
##  <a name="cfixedstringt"></a>CFixedStringT::CFixedStringT  
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
 `psz`  
 以 null 结尾的字符串复制到此`CFixedStringT`对象。  
  
 `str`  
 现有`CFixedStringT`要复制到此对象`CFixedStringT`对象。  
  
 `pStringMgr`  
 指向的内存管理器的指针`CFixedStringT`对象。 有关详细信息`IAtlStringMgr`和内存管理`CFixedStringT`，请参阅[内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
### <a name="remarks"></a>备注  
 因为构造函数将输入的数据复制到新的已分配存储，您应该知道可能会导致异常的内存。 请注意，某些这些构造函数成为转换函数。  
  
##  <a name="operator__eq"></a>CFixedStringT::operator =  
 重新初始化现有`CFixedStringT`用新数据的对象。  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>参数  
 `str`  
 以 null 结尾的字符串复制到此`CFixedStringT`对象。  
  
 `psz`  
 现有`CFixedStringT`要被复制到此`CFixedStringT`对象。  
  
### <a name="remarks"></a>备注  
 您应该知道可能会发生异常，只要您使用赋值运算符，因为通常分配新存储来存放所生成的内存`CFixedStringT`对象。  
  
## <a name="see-also"></a>另请参阅  
 [CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)





