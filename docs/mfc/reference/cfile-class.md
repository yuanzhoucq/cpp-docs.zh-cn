---
title: CFile 类
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: 53afaf7732811e25729944eb71130a88e4f17a87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754999"
---
# <a name="cfile-class"></a>CFile 类

Microsoft 基础类文件类的基类。

## <a name="syntax"></a>语法

```
class CFile : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[文件文件：文件](#cfile)|从路径或`CFile`文件句柄构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[文件文件：：中止](#abort)|关闭忽略所有警告和错误的文件。|
|[文件文件：关闭](#close)|关闭文件并删除对象。|
|[文件：:D](#duplicate)|基于此文件构造重复的对象。|
|[文件文件：：冲洗](#flush)|刷新尚未写入的任何数据。|
|[文件文件：获取文件名称](#getfilename)|检索所选文件的文件名。|
|[文件文件：获取文件路径](#getfilepath)|检索所选文件的完整文件路径。|
|[文件文件：获取文件标题](#getfiletitle)|检索所选文件的标题。|
|[文件文件：获取长度](#getlength)|检索文件的长度。|
|[文件文件：获取位置](#getposition)|检索当前文件指针。|
|[文件文件：获取状态](#getstatus)|检索打开文件的状态，或在静态版本中检索指定文件的状态（静态、虚拟函数）。|
|[文件文件：锁定范围](#lockrange)|锁定文件中的字节范围。|
|[文件文件：：打开](#open)|使用错误测试选项安全地打开文件。|
|[文件文件：阅读](#read)|在当前文件位置从文件读取（未缓冲）数据。|
|[文件文件：：删除](#remove)|删除指定的文件（静态函数）。|
|[文件文件：重命名](#rename)|重命名指定的文件（静态函数）。|
|[文件文件：寻找](#seek)|定位当前文件指针。|
|[文件文件：：寻求开始](#seektobegin)|将当前文件指针定位在文件的开头。|
|[文件文件：：寻求结束](#seektoend)|将当前文件指针定位到文件的末尾。|
|[文件文件：设置文件路径](#setfilepath)|设置所选文件的完整文件路径。|
|[文件文件：：设置长度](#setlength)|更改文件的长度。|
|[文件文件：：设置状态](#setstatus)|设置指定文件（静态虚拟函数）的状态。|
|[文件文件：解锁范围](#unlockrange)|解锁文件中的字节范围。|
|[文件文件：写入](#write)|将文件中的数据（未缓冲）写入当前文件位置。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[文件文件：：操作员手柄](#operator_handle)|`CFile`对象的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[文件：：h卷](#hfilenull)|确定`CFile`对象是否具有有效的句柄。|
|[文件：：m_hFile](#m_hfile)|通常包含操作系统文件句柄。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[文件：：m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 对象的指针。|

## <a name="remarks"></a>备注

它直接提供未缓冲的二进制磁盘输入/输出服务，并通过派生类间接支持文本文件和内存文件。 `CFile`与`CArchive`类结合使用，以支持 Microsoft 基础类对象的序列化。

此类与其派生类之间的分层关系允许程序通过多态接口`CFile`对所有文件对象进行操作。 例如，内存文件就像磁盘文件一样。

通用`CFile`磁盘 I/O 的用途及其派生类。 对`ofstream`发送到磁盘文件的`iostream`格式化文本使用或其他 Microsoft 类。

通常，磁盘文件在构造时`CFile`自动打开，并在销毁时关闭。 静态成员函数允许您在不打开文件的情况下询问文件的状态。

`CFile`有关使用 的详细信息，请参阅[MFC](../../mfc/files-in-mfc.md)中的文章文件和*运行时库参考*中[的文件处理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cfileabort"></a><a name="abort"></a>文件文件：：中止

关闭与此对象关联的文件，并使该文件无法读取或写入。

```
virtual void Abort();
```

### <a name="remarks"></a>备注

如果在销毁对象之前尚未关闭该文件，析构函数将为您关闭该文件。

在处理异常时，`CFile::Abort`有`CFile::Close`两个重要方面的不同。 首先，`Abort`函数不会在失败时引发异常，因为 失败被`Abort`忽略。 其次，`Abort`如果文件尚未打开或以前已关闭，则无法**断言**。

如果使用**new**在堆上`CFile`分配对象，则必须在关闭文件后将其删除。 `Abort`集`m_hFile`到`CFile::hFileNull`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>文件文件：文件

构造并初始化一个 `CFile` 对象。

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>参数

*hFile*<br/>
要附加到 `CFile` 对象的文件的句柄。

*lpszFile名称*<br/>
要附加到 `CFile` 对象的文件的相对路径或完整路径。

*nOpenFlags*<br/>
指定文件的文件访问选项的按位组合 (OR)。 有关可能的选项，请参阅“备注”部分。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

以下五个表列出了*nOpenFlags*参数的可能选项。

仅选择下列文件访问模式选项之一。 默认文件访问模式为 `CFile::modeRead`，该模式为只读模式。

|“值”|说明|
|-----------|-----------------|
|`CFile::modeRead`|只请求读取访问权限。|
|`CFile::modeWrite`|只请求写入访问权限。|
|`CFile::modeReadWrite`|请求读写访问权限。|

选择以下字符模式选项之一。

|“值”|说明|
|-----------|-----------------|
|`CFile::typeBinary`|设置二元模式（仅在派生类中使用）。|
|`CFile::typeText`|设置带有特殊处理回车换行对的文本模式（仅在派生类中使用）。|
|`CFile::typeUnicode`|设置 Unicode 模式（仅在派生类中使用）。 当应用程序在 Unicode 配置中生成时，文本将以 Unicode 格式写入文件中。 不会将 BOM 写入该文件中。|

仅选择下列文件共享模式选项之一。 默认文件共享模式为 `CFile::shareExclusive`，该模式是独占模式。

|“值”|说明|
|-----------|-----------------|
|`CFile::shareDenyNone`|没有任何共享限制。|
|`CFile::shareDenyRead`|拒绝向所有其他用户提供读取访问权限。|
|`CFile::shareDenyWrite`|拒绝向所有其他用户提供写入访问权限。|
|`CFile::shareExclusive`|拒绝向所有其他用户提供读写访问权限。|

选择下面的第一个（或全选）文件创建模式选项。 默认创建模式为 `CFile::modeNoTruncate`，该模式当前处于打开状态。

|“值”|说明|
|-----------|-----------------|
|`CFile::modeCreate`|如果没有文件，则创建新文件。 如果文件已存在，则该文件将被覆盖，最初设置为零长度。|
|`CFile::modeNoTruncate`|如果不存在文件，则创建新文件;否则，如果文件已存在，则该文件将附加到对象`CFile`。|

按照描述选择以下文件缓存选项。 默认情况下，系统使用一个通用缓存方案，该方案不能作为选项提供。

|“值”|说明|
|-----------|-----------------|
|`CFile::osNoBuffer`|系统不为文件使用中间缓存。 此选项取消以下 2 个选项。|
|`CFile::osRandomAccess`|文件缓存针对随机访问进行了优化。 不要同时使用此选项和顺序扫描选项。|
|`CFile::osSequentialScan`|文件缓存针对顺序访问进行了优化。 不要同时使用此选项和随机访问选项。|
|`CFile::osWriteThrough`|写入操作无需延迟完成。|

选择下列安全选项以防止继承文件句柄。 默认情况下，所有新的子进程都可以使用文件句柄。

|“值”|说明|
|-----------|-----------------|
|`CFile::modeNoInherit`|阻止任何子进程使用文件句柄。|

默认构造函数初始化成员，但不会将文件附加到`CFile`对象。 使用此构造函数后，使用[CFile：：open](#open)方法打开文件并将其附加到`CFile`对象。

带有一个参数的构造函数将初始化成员，并且将现有文件附加到 `CFile` 对象。

带有两个参数的构造函数将初始化成员并尝试打开指定文件。 若此构造函数成功打开指定文件，则该文件将附加到 `CFile` 对象；否则，此构造函数将引发指向 `CInvalidArgException` 对象的指针。 有关如何处理异常的详细信息，请参阅[异常](../../mfc/exception-handling-in-mfc.md)。

如果`CFile`对象成功打开指定的文件，它将在`CFile`销毁对象时自动关闭此文件;如果对象成功打开指定文件，则该对象将在对象销毁时自动关闭此文件。否则，必须在文件不再附加到对象后显式关闭该文件`CFile`。

### <a name="example"></a>示例

下面的代码演示如何使用 `CFile`。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>文件文件：关闭

关闭与此对象关联的文件，并使该文件无法读取或写入。

```
virtual void Close();
```

### <a name="remarks"></a>备注

如果在销毁对象之前尚未关闭该文件，析构函数将为您关闭该文件。

如果使用**new**在堆上`CFile`分配对象，则必须在关闭文件后将其删除。 `Close`集`m_hFile`到`CFile::hFileNull`。

### <a name="example"></a>示例

请参阅[CFile 的示例：：CFile](#cfile)。

## <a name="cfileduplicate"></a><a name="duplicate"></a>文件：:D

为给定文件构造`CFile`重复的对象。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>返回值

指向重复`CFile`对象的指针。

### <a name="remarks"></a>备注

此函数等效于 C 运行时函数`_dup`。

## <a name="cfileflush"></a><a name="flush"></a>文件文件：：冲洗

强制将文件缓冲区中剩余的任何数据写入文件。

```
virtual void Flush();
```

### <a name="remarks"></a>备注

的使用`Flush`并不能保证缓冲区的`CArchive`刷新。 如果您使用的是存档，请先调用[CArchive：：Flush。](../../mfc/reference/carchive-class.md#flush)

### <a name="example"></a>示例

请参阅[CFile 的示例：设置文件路径](#setfilepath)。

## <a name="cfilegetfilename"></a><a name="getfilename"></a>文件文件：获取文件名称

调用此成员函数以检索指定文件的名称。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>返回值

文件的名称。

### <a name="remarks"></a>备注

例如，当您调用`GetFileName`以生成有关文件`c:\windows\write\myfile.wri`的消息时，将返回文件名 。 `myfile.wri`

要返回文件的整个路径（包括名称），请调用[GetFilePath](#getfilepath)。 要返回文件的标题 （），`myfile`请调用[GetFileTitle](#getfiletitle)。

### <a name="example"></a>示例

此代码片段将打开 SYSTEM。在 WINDOWS 目录中的 INI 文件。 如果找到，该示例将打印出名称、路径和标题，如"输出"所示：

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>文件文件：获取文件路径

调用此成员函数以检索指定文件的完整路径。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>返回值

指定文件的完整路径。

### <a name="remarks"></a>备注

例如，当您调用`GetFilePath`以生成有关文件`c:\windows\write\myfile.wri`的消息时，将返回文件路径 。 `c:\windows\write\myfile.wri`

要仅返回文件的名称 （），`myfile.wri`请调用[GetFileName](#getfilename)。 要返回文件的标题 （），`myfile`请调用[GetFileTitle](#getfiletitle)。

### <a name="example"></a>示例

请参阅[GetFileName 的示例](#getfilename)。

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>文件文件：获取文件标题

调用此成员函数以检索文件的文件标题（显示名称）。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>返回值

基础文件的标题。

### <a name="remarks"></a>备注

此方法调用[GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)来检索文件的标题。 如果成功，该方法将返回系统用于向用户显示文件名的字符串。 否则，该方法将调用[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)来检索基础文件的文件名（包括文件扩展名）。 这意味着文件扩展名并不总是包含在返回的文件标题字符串中。 有关详细信息，请参阅在 Windows SDK 中[获取文件标题](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)和[路径查找文件名称](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

要返回文件的整个路径（包括名称），请调用[GetFilePath](#getfilepath)。 要仅返回文件的名称，请调用[GetFileName](#getfilename)。

### <a name="example"></a>示例

请参阅[GetFileName 的示例](#getfilename)。

## <a name="cfilegetlength"></a><a name="getlength"></a>文件文件：获取长度

获取文件的当前逻辑长度（以字节为单位）。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

文件的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>文件文件：获取位置

获取文件指针的当前值，可用于以后对`Seek`的调用。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>返回值

文件指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>文件文件：获取状态

此方法检索与给定`CFile`对象实例或给定文件路径相关的状态信息。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*rStatus*<br/>
对将接收状态信息的用户提供`CFileStatus`的结构的引用。 结构`CFileStatus`具有以下字段：

- `CTime m_ctime`创建文件的日期和时间。

- `CTime m_mtime`上次修改文件的日期和时间。

- `CTime m_atime`上次访问文件的日期和时间进行读取。

- `ULONGLONG m_size`文件的逻辑大小（以字节为单位），由 DIR 命令报告。

- `BYTE m_attribute`文件的属性字节。

- `char m_szFullName[_MAX_PATH]`Windows 字符集中的绝对文件名。

*lpszFile名称*<br/>
Windows 字符集中的字符串，它是所需文件的路径。 路径可以是相对路径，也可以是绝对路径，也可以包含网络路径名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="return-value"></a>返回值

如果成功获取指定文件的状态信息，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

非静态版本的`GetStatus`检索与给定`CFile`对象关联的打开文件的状态信息。  的`GetStatus`静态版本从给定的文件路径获取文件状态，而无需实际打开文件。 此版本可用于测试文件的存在和访问权限。

结构`m_attribute`的成员`CFileStatus`引用文件属性集。 类`CFile`提供**属性**枚举类型，以便可以象征性地指定文件属性：

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>文件：：h卷

确定`CFile`对象的有效文件句柄是否存在。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>备注

此常量用于确定`CFile`对象是否具有有效的文件句柄。

以下示例演示此操作：

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>文件文件：锁定范围

锁定打开文件中的字节范围，如果文件已锁定，则引发异常。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>参数

*德波普斯*<br/>
要锁定的字节范围开始字节偏移。

*dwCount*<br/>
要锁定的范围中的字节数。

### <a name="remarks"></a>备注

锁定文件中的字节将阻止其他进程访问这些字节。 可以锁定文件的多个区域，但不允许重叠区域。

使用`UnlockRange`成员函数解锁区域时，字节范围必须与以前锁定的区域完全对应。 函数`LockRange`不合并相邻区域。 如果两个锁定区域相邻，则必须单独解锁每个区域。

> [!NOTE]
> 此函数不适用于派生类`CMemFile`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>文件：：m_hFile

包含打开文件的操作系统文件句柄。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>备注

`m_hFile`是 UINT 类型的公共变量。 它包含`CFile::hFileNull`，如果尚未分配句柄，则包含与操作系统无关的空文件指示器。

不建议`m_hFile`使用，因为成员的含义取决于派生类。 `m_hFile`为方便公众支持非多态使用类。

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>文件：：m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

## <a name="cfileopen"></a><a name="open"></a>文件文件：：打开

已重载。 `Open`设计用于默认`CFile`构造函数。

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
包含所需文件的路径的字符串。 路径可以是相对的、绝对的还是网络名称 （UNC）。

*nOpenFlags*<br/>
定义文件的共享和访问模式的 UINT。 它指定打开文件时要执行的操作。 您可以使用位OR （ **&#124;** ） 运算符组合选项. 需要一个访问权限和一个共享选项;`modeCreate`和`modeNoInherit`模式是可选的。 有关模式选项的列表，请参阅[CFile](#cfile)构造函数。

*pError*<br/>
指向将接收失败操作状态的现有文件异常对象的指针。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="return-value"></a>返回值

如果打开成功，则非零;否则 0。 仅当返回 0 时 *，pError*参数才有意义。

### <a name="remarks"></a>备注

这两`Open`个函数是打开文件的"安全"方法，其中故障是正常的预期条件。

当构造`CFile`函数在错误条件下引发异常时，`Open`返回 FALSE 以查找错误条件。 `Open`但是，仍然可以初始化[CFileException](../../mfc/reference/cfileexception-class.md)对象来描述错误。 如果不提供*pError*参数，或者为*pError*传递 NULL，`Open`则返回 FALSE，并且不引发 。 `CFileException` 如果将指针传递给现有`CFileException`，并且`Open`遇到错误，则函数将填充描述该错误的信息。 `Open`在这两种情况下，都不会引发异常。

下表描述了 的`Open`可能结果。

|`pError`|遇到错误|返回值|文件例外内容|
|--------------|------------------------|------------------|----------------------------|
|Null|否|TRUE|不适用|
|ptr 到`CFileException`|否|TRUE|未更改|
|Null|是|FALSE|不适用|
|ptr 到`CFileException`|是|FALSE|初始化以描述错误|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>文件文件：：操作员手柄

使用此运算符将`CFile`句柄传递给对象，以将[读取文件Ex](/windows/win32/api/fileapi/nf-fileapi-readfileex)和[GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime)等函数传递给预期`HANDLE`中的函数。

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>文件文件：阅读

从与对象关联的文件中将数据读取到缓冲区中`CFile`。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向用户提供的缓冲区的指针，该缓冲区用于接收从文件读取的数据。

*nCount*<br/>
要从文件读取的最大字节数。 对于文本模式文件，车厢返回行馈送对计为单个字符。

### <a name="return-value"></a>返回值

传输到缓冲区的字节数。 对于所有`CFile`类，如果达到文件结尾，返回值可能小于*nCount。*

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

有关另一个示例，请参阅[CFile：：打开](#open)。

## <a name="cfileremove"></a><a name="remove"></a>文件文件：：删除

此静态函数删除路径指定的文件。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
是所需文件的路径的字符串。 路径可以是相对的，也可以是绝对的，并且可以包含网络名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

`Remove`不会删除目录。

如果`Remove`连接的文件处于打开状态或无法删除该文件，则成员函数将引发异常。 此函数等效于 DEL 命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>文件文件：重命名

此静态函数重命名指定的文件。

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpszOld名称*<br/>
老路

*lpsz 新名称*<br/>
新路径。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

无法重命名目录。 此函数等效于 REN 命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>文件文件：寻找

在打开的文件中重新定位文件指针。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>参数

*lOff*<br/>
要移动文件指针的字节数。 正值将文件指针移动到文件末尾;负值将文件指针移动到文件开头。

*n 从*<br/>
位置寻求。 有关可能的值，请参阅备注部分。

### <a name="return-value"></a>返回值

如果方法成功，则文件指针的位置;否则，返回值未定义，并引发指向异常的`CFileException`指针。

### <a name="remarks"></a>备注

下表列出了*nFrom*参数的可能值。

|“值”|说明|
|-----------|-----------------|
|`CFile::begin`|从文件的开头查找。|
|`CFile::current`|从文件指针的当前位置查找。|
|`CFile::end`|从文件末尾查找。|

打开文件时，文件指针定位在 0，即文件的开头。

您可以将文件指针设置为文件末尾以外的位置。 如果这样做，则文件的大小不会增加，直到您写入该文件。

此方法的异常处理程序必须在处理异常后删除异常对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>文件文件：：寻求开始

将文件指针的值设置到文件的开头。

```cpp
void SeekToBegin();
```

### <a name="remarks"></a>备注

`SeekToBegin()` 等效于 `Seek( 0L, CFile::begin )`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>文件文件：：寻求结束

将文件指针的值设置到文件的逻辑端。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>返回值

文件的长度（以字节为单位）。

### <a name="remarks"></a>备注

`SeekToEnd()` 等效于 `CFile::Seek( 0L, CFile::end )`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>文件文件：设置文件路径

调用此函数以指定文件的路径。 例如，如果在构造[CFile](../../mfc/reference/cfile-class.md)对象时文件的路径不可用，请调用`SetFilePath`以提供该文件。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>参数

*lpsz 新名称*<br/>
指向指定新路径的字符串的指针。

### <a name="remarks"></a>备注

> [!NOTE]
> `SetFilePath`不打开文件或创建文件;它只是将`CFile`对象与路径名称关联，然后可以使用路径名称。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>文件文件：：设置长度

调用此函数以更改文件的长度。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>参数

*德纽伦*<br/>
文件所需的长度（以字节为单位）。 此值可以大于或小于文件的当前长度。 文件将根据需要扩展或截断。

### <a name="remarks"></a>备注

> [!NOTE]
> 使用`CMemFile`时，此函数可以`CMemoryException`引发对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>文件文件：：设置状态

设置与此文件位置关联的文件的状态。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpszFile名称*<br/>
是所需文件的路径的字符串。 路径可以是相对的，也可以是绝对的，并且可以包含网络名称。

*status*<br/>
包含新状态信息的缓冲区。 调用`GetStatus`成员函数以用当前值预`CFileStatus`填结构，然后根据需要进行更改。 如果值为 0，则相应的状态项不会更新。 有关`CFileStatus`结构的说明，请参阅[GetStatus](#getstatus)成员函数。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

要设置时间，请修改`m_mtime`*状态*字段 。

当您调用`SetStatus`以尝试仅更改文件的属性，并且文件状态结构`m_mtime`的成员是非零时，属性也可能受到影响（更改时间戳可能对属性产生副作用）。 如果只想更改文件的属性，请先将`m_mtime`文件状态结构的成员设置为零，然后调用`SetStatus`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>文件文件：解锁范围

解锁打开文件中的字节范围。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>参数

*德波普斯*<br/>
要解锁的字节范围开始的字节偏移。

*dwCount*<br/>
要解锁的范围中的字节数。

### <a name="remarks"></a>备注

有关详细信息，请参阅[LockRange](#lockrange)成员函数的说明。

> [!NOTE]
> 此函数不适用于派生类`CMemFile`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>文件文件：写入

将数据从缓冲区写入与`CFile`对象关联的文件。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向用户提供的缓冲区的指针，其中包含要写入文件的数据。

*nCount*<br/>
要从缓冲区传输的字节数。 对于文本模式文件，车厢返回行馈送对计为单个字符。

### <a name="remarks"></a>备注

`Write`引发一个异常以响应多个条件，包括磁盘满型条件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

另请参阅[CFile 的示例：：CFile](#cfile)和[CFile：：打开](#open)。

## <a name="see-also"></a>请参阅

[MFC 样品 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 类](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 类](../../mfc/reference/cmemfile-class.md)
