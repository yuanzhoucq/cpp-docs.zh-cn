---
title: "CLongBinary 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB
- CLongBinary
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object)
- CLongBinary class
- BLOB (binary large object), CLongBinary class
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
caps.latest.revision: 21
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: bb73604ee4d15f3a71be8514f348ad265064928a
ms.lasthandoff: 02/24/2017

---
# <a name="clongbinary-class"></a>CLongBinary 类
简化对数据库中超大二进制数据对象（经常称作 BLOB，即“二进制大对象”）的使用。  
  
## <a name="syntax"></a>语法  
  
```  
class CLongBinary : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](#clongbinary)|构造 `CLongBinary` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|包含以字节为单位的句柄存储在数据对象的实际大小`m_hData`。|  
|[CLongBinary::m_hData](#m_hdata)|包含 Windows`HGLOBAL`实际的图像对象的句柄。|  
  
## <a name="remarks"></a>备注  
 例如，SQL 表中的记录字段可能包含表示图片的位图。 一个`CLongBinary`对象将存储此类对象并跟踪其大小。  
  
> [!NOTE]
>  通常情况下，最好将更好的做法现在使用[CByteArray](../../mfc/reference/cbytearray-class.md)结合[DFX_Binary](http://msdn.microsoft.com/library/678021a3-2e46-44d7-8528-71bb692dcc07)函数。 您仍然可以使用`CLongBinary`，但一般来说`CByteArray`将提供更多功能在 Win32 下，由于不再使用 16 位时遇到的大小限制`CByteArray`。 这个建议都适用于与数据访问对象 (DAO)，以及开放式数据库连接 (ODBC) 进行编程。  
  
 若要使用`CLongBinary`对象，将声明类型的字段数据成员`CLongBinary`记录集类中。 此成员将嵌入的成员的记录集类，则在构造该记录集时，将构造。 之后`CLongBinary`构造对象时，记录字段交换 (RFX) 机制从数据源上的当前记录中的字段中加载数据对象，并将其存储回该记录时将更新该记录。 RFX 查询数据源中的二进制大型对象，大小为其分配存储 (通过`CLongBinary`对象的`m_hData`数据成员)，并将存储`HGLOBAL`中的数据的句柄`m_hData`。 RFX 还存储此数据对象中的实际大小`m_dwDataLength`数据成员。 通过对象中的数据处理`m_hData`，使用相同的方法通常用于处理存储在 Windows 中的数据`HGLOBAL`处理。  
  
 当破坏您的记录集中的嵌入式`CLongBinary`对象也将被销毁，并其析构函数释放`HGLOBAL`数据句柄。  
  
 有关大型对象和使用情况的详细信息`CLongBinary`，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)和[记录集︰ 处理大数据项目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdb_.h  
  
##  <a name="a-nameclongbinarya--clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary  
 构造 `CLongBinary` 对象。  
  
```  
CLongBinary();
```  
  
##  <a name="a-namemdwdatalengtha--clongbinarymdwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength  
 以字节为单位的存储中的数据存储的实际大小`HGLOBAL`以处理`m_hData`。  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>备注  
 此大小可能小于分配的数据的内存块的大小。 调用 Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593)函数可获取的已分配的大小。  
  
##  <a name="a-namemhdataa--clongbinarymhdata"></a><a name="m_hdata"></a>CLongBinary::m_hData  
 存储 Windows`HGLOBAL`实际的二进制大型对象数据的句柄。  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)

