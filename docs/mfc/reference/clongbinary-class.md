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
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370139"
---
# <a name="clongbinary-class"></a>CLongBinary 类

简化对数据库中超大二进制数据对象（经常称作 BLOB，即“二进制大对象”）的使用。

## <a name="syntax"></a>语法

```
class CLongBinary : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[龙二元：CLongBinary](#clongbinary)|构造 `CLongBinary` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CLongBinary：：m_dwDataLength](#m_dwdatalength)|包含其句柄存储在 中`m_hData`的数据对象的实际大小（以字节为单位）。|
|[CLongBinary：：m_hData](#m_hdata)|包含实际图像对象的 Windows HGLOBAL 句柄。|

## <a name="remarks"></a>备注

例如，SQL 表中的记录字段可能包含表示图片的位图。 对象`CLongBinary`存储此类对象并跟踪其大小。

> [!NOTE]
> 通常，现在最好将[CByteArray](../../mfc/reference/cbytearray-class.md)与[DFX_Binary](record-field-exchange-functions.md#dfx_binary)函数结合使用。 您仍可以使用`CLongBinary`，但通常`CByteArray`在 Win32 下提供了更多功能，因为 16 位`CByteArray`不再遇到大小限制。 此建议适用于数据访问对象 （DAO） 和开放数据库连接 （ODBC） 编程。

要使用`CLongBinary`对象，请声明记录集类中类型的`CLongBinary`字段数据成员。 此成员将是记录集类的嵌入成员，将在构造记录集时构造。 构造`CLongBinary`对象后，记录字段交换 （RFX） 机制从数据源上的当前记录中的字段加载数据对象，并在更新记录时将其存储回记录。 RFX 查询二进制大型对象大小的数据源，为其分配存储（`CLongBinary`通过对象`m_hData`的数据成员），并将`HGLOBAL`句柄存储到 中`m_hData`的数据。 RFX 还会将数据对象的实际大小存储在数据成员中`m_dwDataLength`。 使用与通常用于操作存储在 Windows`m_hData``HGLOBAL`句柄中的数据相同的技术处理对象中的数据。

销毁记录集时，嵌入`CLongBinary`的对象也会被销毁，其析构函数将解构器解分配`HGLOBAL`数据句柄。

有关大型对象和使用的详细信息`CLongBinary`，请参阅[记录集 （ODBC）](../../data/odbc/recordset-odbc.md)和[记录集：使用大型数据项 （ODBC） 的文章](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>要求

**标题：** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>龙二元：CLongBinary

构造 `CLongBinary` 对象。

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary：：m_dwDataLength

以 存储在 HGLOBAL 句柄中的数据的实际大小以字节`m_hData`为单位。

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>备注

此大小可能小于为数据分配的内存块的大小。 调用 Win32 [GLobalSize 函数](/windows/win32/api/winbase/nf-winbase-globalsize)以获取分配的大小。

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary：：m_hData

将 Windows HGLOBAL 句柄存储到实际的二进制大型对象数据。

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)
