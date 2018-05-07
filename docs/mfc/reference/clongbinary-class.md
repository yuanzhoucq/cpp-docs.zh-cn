---
title: CLongBinary 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs:
- C++
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7030fdcb59166c0e70a7b2c2471273c913fe459
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
|[CLongBinary::m_hData](#m_hdata)|包含 Windows`HGLOBAL`实际映像对象的句柄。|  
  
## <a name="remarks"></a>备注  
 例如，SQL 表中的记录字段可能包含表示图片的位图。 A`CLongBinary`对象将存储此类对象和跟踪其大小。  
  
> [!NOTE]
>  通常情况下，是更好的做法现在使用[CByteArray](../../mfc/reference/cbytearray-class.md)结合[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函数。 你仍然可以使用`CLongBinary`，但一般而言`CByteArray`提供更多的功能在 Win32 下，由于没有不再遇到的 16 位的大小限制`CByteArray`。 此建议适用于通过数据访问对象 (DAO) 和开放式数据库连接 (ODBC) 进行编程。  
  
 若要使用`CLongBinary`对象，声明类型的字段数据成员`CLongBinary`记录集类中。 此成员将记录集类的嵌入的成员，将构造构造记录集。 后`CLongBinary`构造对象时，记录字段交换 (RFX) 机制从数据源上的当前记录中的字段中加载的数据对象，并将其存储回记录时将更新该记录。 RFX 查询数据源的二进制大型对象，大小为其分配存储 (通过`CLongBinary`对象的`m_hData`数据成员)，并将存储`HGLOBAL`中的数据的句柄`m_hData`。 RFX 还存储中的数据对象的实际大小`m_dwDataLength`数据成员。 使用中的数据对象，通过`m_hData`，使用你通常用来处理存储在 Windows 中的数据的相同技术`HGLOBAL`处理。  
  
 当销毁记录集，嵌入`CLongBinary`对象也会被销毁，并其析构函数释放`HGLOBAL`数据句柄。  
  
 有关大型对象和用法的详细信息`CLongBinary`，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)和[记录集： 处理大数据项目 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdb_.h  
  
##  <a name="clongbinary"></a>  CLongBinary::CLongBinary  
 构造 `CLongBinary` 对象。  
  
```  
CLongBinary();
```  
  
##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength  
 以字节为单位的存储中的数据存储的实际大小`HGLOBAL`在中处理`m_hData`。  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>备注  
 此大小可能小于为数据分配的内存块的大小。 调用 Win32 [GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593)函数可获取分配的大小。  
  
##  <a name="m_hdata"></a>  CLongBinary::m_hData  
 存储 Windows`HGLOBAL`实际的二进制大型对象数据的句柄。  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)
