---
title: CBookmark 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7a2eaaf273bb2c0ae4f3ab297fe444a41e81c873
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058050"
---
# <a name="cbookmark-class"></a>CBookmark 类

在其缓冲区中保存的书签值。  
  
## <a name="syntax"></a>语法

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
### <a name="parameters"></a>参数  

*nSize*<br/>
以字节为单位的书签缓冲区的大小。 当*nSize*为零，将在运行时动态创建书签缓冲区。  

## <a name="requirements"></a>要求  

**标头:** atldbcli.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CBookmark](#cbookmark)|构造函数|  
|[GetBuffer](#getbuffer)|检索指向缓冲区的指针。|  
|[GetSize](#getsize)|检索以字节为单位的缓冲区的大小。|  
|[SetBookmark](#setbookmark)|设置书签值。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator =](#operator)|将分配一个`CBookmark`到另一个类。|  
  
## <a name="remarks"></a>备注  

`CBookmark<0>` 模板专用化的`CBookmark`; 在运行时动态创建其缓冲区。  

## <a name="cbookmark"></a> Cbookmark:: Cbookmark

构造函数。  
  
### <a name="syntax"></a>语法  
  
```cpp
CBookmark();
   
CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>参数  

*nSize*<br/>
[in] 书签缓冲区的大小（以字节为单位）。  
  
### <a name="remarks"></a>备注  

第一个函数将缓冲区设置为 NULL，而缓冲区大小为 0。 第二个函数将缓冲区大小设置为*nSize*，并为字节数组的缓冲区*nSize*字节。  
  
> [!NOTE]
>  此函数选项仅适用于`CBookmark<0>`。 
  
## <a name="getbuffer"></a> Cbookmark:: Getbuffer

检索书签缓冲区的指针。  
  
### <a name="syntax"></a>语法  
  
```cpp
virtual BYTE* GetBuffer() const throw();  
```  
  
### <a name="return-value"></a>返回值  

指向书签缓冲区的指针。 

## <a name="getsize"></a> Cbookmark:: Getsize

检索书签缓冲区的大小。  
  
### <a name="syntax"></a>语法  
  
```cpp
virtual DBLENGTH GetSize() const throw();  
```  
  
### <a name="return-value"></a>返回值  

缓冲区的大小（以字节为单位）。  

## <a name="setbookmark"></a> Cbookmark:: Setbookmark

将书签值引用的复制*pBuffer*到`CBookmark`缓冲和缓冲区大小设置为*nSize*。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();  
```  
  
#### <a name="parameters"></a>参数  

*nSize*<br/>
[in]书签缓冲区的大小。  
  
*pBuffer*<br/>
[in]指向包含书签值的字节数组的指针。  
  
### <a name="return-value"></a>返回值  

标准的 HRESULT。  
  
### <a name="remarks"></a>备注  

此函数选项仅适用于`CBookmark<0>`。 

## <a name="operator"></a> Cbookmark:: Operator =

将一个 `CBookmark` 对象分配给其他对象。  
  
### <a name="syntax"></a>语法  
  
```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();  
```  
  
### <a name="remarks"></a>备注  

仅在需要此运算符`CBookmark<0>`。   

## <a name="see-also"></a>请参阅  

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)