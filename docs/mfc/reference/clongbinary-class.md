---
title: CLongBinary 类
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: ed3a153ec89785a9c9da43037d20f7d88b5661ff
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260707"
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
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|包含的实际大小以字节为单位的数据对象的句柄存储在`m_hData`。|
|[CLongBinary::m_hData](#m_hdata)|包含实际的图像对象的 Windows HGLOBAL 句柄。|

## <a name="remarks"></a>备注

例如，SQL 表中的记录字段可能包含表示图片的位图。 一个`CLongBinary`对象将存储此类对象并跟踪其大小。

> [!NOTE]
>  一般情况下，它是更好的做法现在使用[CByteArray](../../mfc/reference/cbytearray-class.md)结合[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函数。 您仍然可以使用`CLongBinary`，但一般情况下`CByteArray`提供更多的功能，在 Win32 下，由于没有长度不能，遇到一个具有 16 位的大小限制`CByteArray`。 此建议适用于与数据访问对象 (DAO)，以及开放式数据库连接 (ODBC) 的编程。

若要使用`CLongBinary`对象，声明类型的字段数据成员`CLongBinary`记录集类中。 此成员将是记录集类的嵌入的成员，并构造该记录集时将构造。 之后`CLongBinary`构造对象、 记录字段交换 (RFX) 机制从数据源上的当前记录中的字段中加载的数据对象并将其存储回记录时将更新该记录。 RFX 的二进制大型对象的大小为其分配存储查询数据源 (通过`CLongBinary`对象的`m_hData`数据成员)，并将存储`HGLOBAL`中的数据的句柄`m_hData`。 RFX 还会将存储此数据对象中的实际大小`m_dwDataLength`数据成员。 使用通过对象中的数据`m_hData`，使用相同的方法通常用于处理在 Windows 中存储的数据`HGLOBAL`处理。

当销毁记录集，嵌入`CLongBinary`还销毁对象时，和它的析构函数释放`HGLOBAL`数据句柄。

有关大型对象和使用的详细信息`CLongBinary`，请参阅文章[记录集 (ODBC)](../../data/odbc/recordset-odbc.md)和[记录集：处理大数据项 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。

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

以字节为单位的 HGLOBAL 句柄中存储的数据存储的实际大小`m_hData`。

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>备注

此大小可能小于分配的数据的内存块的大小。 调用 Win32 [GLobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize)函数以获取已分配的大小。

##  <a name="m_hdata"></a>  CLongBinary::m_hData

将存储的 Windows HGLOBAL 句柄的实际二进制大型对象数据。

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
