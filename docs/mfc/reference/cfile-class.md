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
ms.openlocfilehash: a9161764f6c8646766a73add01c25cce5619ad19
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424463"
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
|[CFile：： CFile](#cfile)|使用路径或文件句柄构造 `CFile` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFile：： Abort](#abort)|关闭忽略所有警告和错误的文件。|
|[CFile：： Close](#close)|关闭文件并删除对象。|
|[CFile：:D 重复](#duplicate)|基于此文件构造重复的对象。|
|[CFile：： Flush](#flush)|刷新仍要写入的所有数据。|
|[CFile：： GetFileName](#getfilename)|检索选定文件的文件名。|
|[CFile：： GetFilePath](#getfilepath)|检索所选文件的完整文件路径。|
|[CFile：： GetFileTitle](#getfiletitle)|检索选定文件的标题。|
|[CFile：： GetLength](#getlength)|检索文件的长度。|
|[CFile：： GetPosition](#getposition)|检索当前文件指针。|
|[CFile：： GetStatus](#getstatus)|检索打开文件的状态，或在静态版本中检索指定文件的状态（静态、虚函数）。|
|[CFile：： LockRange](#lockrange)|锁定文件中的字节范围。|
|[CFile：： Open](#open)|使用错误测试选项安全打开文件。|
|[CFile：： Read](#read)|从当前文件位置的文件读取（未缓冲）数据。|
|[CFile：： Remove](#remove)|删除指定的文件（静态函数）。|
|[CFile：： Rename](#rename)|重命名指定的文件（静态函数）。|
|[CFile：： Seek](#seek)|定位当前文件指针。|
|[CFile：： SeekToBegin](#seektobegin)|将当前文件指针定位在文件的开头。|
|[CFile：： SeekToEnd](#seektoend)|将当前文件指针定位到文件末尾。|
|[CFile：： SetFilePath](#setfilepath)|设置所选文件的完整文件路径。|
|[CFile：： SetLength](#setlength)|更改文件的长度。|
|[CFile：： SetStatus](#setstatus)|设置指定文件的状态（静态、虚函数）。|
|[CFile：： UnlockRange](#unlockrange)|解锁文件中的字节范围。|
|[CFile：： Write](#write)|将文件中的数据写入（未缓冲）到当前文件位置。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CFile：： operator 句柄](#operator_handle)|`CFile` 对象的句柄。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CFile：： hFileNull](#hfilenull)|确定 `CFile` 对象是否具有有效的句柄。|
|[CFile：： m_hFile](#m_hfile)|通常包含操作系统文件句柄。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CFile：： m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 对象的指针。|

## <a name="remarks"></a>备注

它直接提供无缓冲的二进制磁盘输入/输出服务，并通过其派生类间接支持文本文件和内存文件。 `CFile` 与 `CArchive` 类结合使用，以支持 Microsoft 基础类对象的序列化。

此类及其派生类之间的层次结构关系允许程序通过多态 `CFile` 接口对所有文件对象进行操作。 例如，内存文件的行为类似于磁盘文件。

使用 `CFile` 及其派生类来实现常规用途的磁盘 i/o。 将 `ofstream` 或其他 Microsoft `iostream` 类用于发送到磁盘文件的格式化文本。

通常，在 `CFile` 构造时自动打开磁盘文件，并在销毁时关闭该文件。 静态成员函数允许您在不打开文件的情况下询问文件状态。

有关使用 `CFile`的详细信息，请参阅《*运行时库参考*中的文章： MFC 和[文件处理](../../c-runtime-library/file-handling.md)中的[文件](../../mfc/files-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="abort"></a>CFile：： Abort

关闭与此对象关联的文件，并使该文件不可用于读取或写入。

```
virtual void Abort();
```

### <a name="remarks"></a>备注

如果在销毁对象之前尚未关闭该文件，则析构函数将关闭该文件。

在处理异常时，`CFile::Abort` 在两个重要方面与 `CFile::Close` 不同。 首先，`Abort` 函数将不会在失败时引发异常，因为 `Abort`忽略失败。 其次，`Abort` 不会**断言**文件是否尚未打开，或以前是否已关闭。

如果使用**new**在堆上分配 `CFile` 对象，则必须在关闭文件后将其删除。 `Abort` 将 `m_hFile` 设置为 `CFile::hFileNull`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>CFile：： CFile

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

### <a name="parameters"></a>parameters

*hFile*<br/>
要附加到 `CFile` 对象的文件的句柄。

*lpszFileName*<br/>
要附加到 `CFile` 对象的文件的相对路径或完整路径。

*nOpenFlags*<br/>
指定文件的文件访问选项的按位组合 (OR)。 有关可能的选项，请参阅“备注”部分。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

以下五个表列出了*nOpenFlags*参数的可能选项。

仅选择下列文件访问模式选项之一。 默认文件访问模式为 `CFile::modeRead`，该模式为只读模式。

|值|说明|
|-----------|-----------------|
|`CFile::modeRead`|只请求读取访问权限。|
|`CFile::modeWrite`|只请求写入访问权限。|
|`CFile::modeReadWrite`|请求读写访问权限。|

选择以下字符模式选项之一。

|值|说明|
|-----------|-----------------|
|`CFile::typeBinary`|设置二元模式（仅在派生类中使用）。|
|`CFile::typeText`|为回车-换行对（仅用于派生类）的特殊处理设置文本模式。|
|`CFile::typeUnicode`|设置 Unicode 模式（仅在派生类中使用）。 当应用程序在 Unicode 配置中生成时，文本将以 Unicode 格式写入文件中。 不会将 BOM 写入该文件中。|

仅选择下列文件共享模式选项之一。 默认文件共享模式为 `CFile::shareExclusive`，该模式是独占模式。

|值|说明|
|-----------|-----------------|
|`CFile::shareDenyNone`|没有任何共享限制。|
|`CFile::shareDenyRead`|拒绝向所有其他用户提供读取访问权限。|
|`CFile::shareDenyWrite`|拒绝向所有其他用户提供写入访问权限。|
|`CFile::shareExclusive`|拒绝向所有其他用户提供读写访问权限。|

选择下面的第一个（或全选）文件创建模式选项。 默认创建模式为 `CFile::modeNoTruncate`，该模式当前处于打开状态。

|值|说明|
|-----------|-----------------|
|`CFile::modeCreate`|如果文件不存在，则创建一个新文件。 如果文件已存在，则会被覆盖，并且最初设置为零长度。|
|`CFile::modeNoTruncate`|如果文件不存在，则创建一个新文件;否则，如果该文件已存在，则会附加到 `CFile` 对象上。|

按照描述选择以下文件缓存选项。 默认情况下，系统使用无法作为选项使用的常规用途缓存方案。

|值|说明|
|-----------|-----------------|
|`CFile::osNoBuffer`|系统不会对文件使用中间缓存。 此选项取消以下 2 个选项。|
|`CFile::osRandomAccess`|文件缓存针对随机访问进行了优化。 不要使用此选项和顺序扫描选项。|
|`CFile::osSequentialScan`|文件缓存针对顺序访问进行了优化。 不要同时使用此选项和 "随机访问" 选项。|
|`CFile::osWriteThrough`|写入操作无需延迟即可完成。|

选择下列安全选项以防止继承文件句柄。 默认情况下，所有新的子进程都可以使用文件句柄。

|值|说明|
|-----------|-----------------|
|`CFile::modeNoInherit`|阻止任何子进程使用文件句柄。|

默认构造函数将初始化成员，但不会将文件附加到 `CFile` 的对象。 使用此构造函数后，请使用[CFile：： open](#open)方法打开文件，并将其附加到 `CFile` 的对象。

带有一个参数的构造函数将初始化成员，并且将现有文件附加到 `CFile` 对象。

带有两个参数的构造函数将初始化成员并尝试打开指定文件。 若此构造函数成功打开指定文件，则该文件将附加到 `CFile` 对象；否则，此构造函数将引发指向 `CInvalidArgException` 对象的指针。 有关如何处理异常的详细信息，请参阅[异常](../../mfc/exception-handling-in-mfc.md)。

如果 `CFile` 对象成功打开指定的文件，它将在销毁 `CFile` 对象时自动关闭此文件;否则，必须在文件不再附加到 `CFile` 对象之后显式关闭该文件。

### <a name="example"></a>示例

下面的代码演示如何使用 `CFile`。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>CFile：： Close

关闭与此对象关联的文件，并使该文件不可用于读取或写入。

```
virtual void Close();
```

### <a name="remarks"></a>备注

如果在销毁对象之前尚未关闭该文件，则析构函数将关闭该文件。

如果使用**new**在堆上分配 `CFile` 对象，则必须在关闭文件后将其删除。 `Close` 将 `m_hFile` 设置为 `CFile::hFileNull`。

### <a name="example"></a>示例

请参阅[CFile：： CFile](#cfile)的示例。

##  <a name="duplicate"></a>CFile：:D 重复

为给定文件构造重复的 `CFile` 对象。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>返回值

指向重复 `CFile` 对象的指针。

### <a name="remarks"></a>备注

此函数等效于 C 运行时函数 `_dup`。

##  <a name="flush"></a>CFile：： Flush

强制将文件缓冲区中剩余的所有数据写入文件。

```
virtual void Flush();
```

### <a name="remarks"></a>备注

使用 `Flush` 不保证刷新 `CArchive` 缓冲区。 如果使用的是存档，请先调用[CArchive：： Flush](../../mfc/reference/carchive-class.md#flush) 。

### <a name="example"></a>示例

请参阅[CFile：： SetFilePath](#setfilepath)的示例。

##  <a name="getfilename"></a>CFile：： GetFileName

调用此成员函数以检索指定文件的名称。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>返回值

文件的名称。

### <a name="remarks"></a>备注

例如，当你调用 `GetFileName` 向用户生成有关文件 `c:\windows\write\myfile.wri`的消息时，将返回文件名 `myfile.wri`。

若要返回文件的完整路径，包括名称，请调用[GetFilePath](#getfilepath)。 若要返回文件的标题（`myfile`），请调用[GetFileTitle](#getfiletitle)。

### <a name="example"></a>示例

此代码段将打开系统。INI 文件。 如果找到，则示例将输出名称、路径和标题，如输出中所示：

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>CFile：： GetFilePath

调用此成员函数以检索指定文件的完整路径。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>返回值

指定文件的完整路径。

### <a name="remarks"></a>备注

例如，当你调用 `GetFilePath` 向用户生成有关文件 `c:\windows\write\myfile.wri`的消息时，将返回文件路径 `c:\windows\write\myfile.wri`。

若要仅返回文件的名称（`myfile.wri`），请调用[GetFileName](#getfilename)。 若要返回文件的标题（`myfile`），请调用[GetFileTitle](#getfiletitle)。

### <a name="example"></a>示例

请参阅[GetFileName](#getfilename)的示例。

##  <a name="getfiletitle"></a>CFile：： GetFileTitle

调用此成员函数以检索文件的文件标题（显示名称）。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>返回值

基础文件的标题。

### <a name="remarks"></a>备注

此方法调用[GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)来检索文件的标题。 如果成功，该方法将返回系统用于向用户显示文件名的字符串。 否则，此方法将调用[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)来检索基础文件的文件名（包括文件扩展名）。 这意味着文件扩展名并非始终包含在返回的文件标题字符串中。 有关详细信息，请参阅 Windows SDK 中的[GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)和[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 。

若要返回文件的完整路径，包括名称，请调用[GetFilePath](#getfilepath)。 若要仅返回文件的名称，请调用[GetFileName](#getfilename)。

### <a name="example"></a>示例

请参阅[GetFileName](#getfilename)的示例。

##  <a name="getlength"></a>CFile：： GetLength

获取文件的当前逻辑长度（以字节为单位）。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

文件的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>CFile：： GetPosition

获取文件指针的当前值，该文件指针可用于稍后调用 `Seek`。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>返回值

文件指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>CFile：： GetStatus

此方法检索与给定 `CFile` 对象实例或给定文件路径相关的状态信息。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>parameters

*rStatus*<br/>
对将接收状态信息的用户提供的 `CFileStatus` 结构的引用。 `CFileStatus` 结构包含以下字段：

- `CTime m_ctime` 创建文件的日期和时间。

- `CTime m_mtime` 上次修改文件的日期和时间。

- `CTime m_atime` 上次访问文件以进行读取的日期和时间。

- `ULONGLONG m_size` 由 DIR 命令报告的文件的逻辑大小（以字节为单位）。

- `BYTE m_attribute` 文件的属性字节。

- `char m_szFullName[_MAX_PATH]` Windows 字符集中的绝对文件名。

*lpszFileName*<br/>
Windows 字符集中的字符串，它是所需文件的路径。 路径可以是相对路径或绝对路径，也可以包含网络路径名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="return-value"></a>返回值

如果成功获取指定文件的状态信息，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

`GetStatus` 的非静态版本检索与给定 `CFile` 对象关联的打开文件的状态信息。  `GetStatus` 的静态版本获取给定文件路径的文件状态，而无需实际打开该文件。 此版本适用于测试文件的存在和访问权限。

`CFileStatus` 结构的 `m_attribute` 成员引用文件属性集。 `CFile` 类提供**属性**枚举类型，因此可以符号指定文件属性：

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

##  <a name="hfilenull"></a>CFile：： hFileNull

确定 `CFile` 对象是否存在有效的文件句柄。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>备注

此常量用于确定 `CFile` 对象是否具有有效的文件句柄。

下面的示例演示了此操作：

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>CFile：： LockRange

锁定打开的文件中的某个字节范围，如果该文件已被锁定，则引发异常。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>parameters

*dwPos*<br/>
要锁定的字节范围起始处的字节偏移量。

*dwCount*<br/>
要锁定的范围中的字节数。

### <a name="remarks"></a>备注

锁定文件中的字节将阻止其他进程访问这些字节。 可以锁定文件的多个区域，但不允许重叠区域。

当你使用 `UnlockRange` 成员函数解锁区域时，字节范围必须完全与以前锁定的区域相对应。 `LockRange` 函数不会合并相邻区域。 如果两个锁定区域相邻，则必须单独解锁每个区域。

> [!NOTE]
>  此函数不适用于 `CMemFile`派生的类。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>CFile：： m_hFile

包含打开的文件的操作系统文件句柄。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>备注

`m_hFile` 是 UINT 类型的公共变量。 它包含与操作系统无关的空文件指示器的 `CFile::hFileNull`（如果尚未分配句柄）。

不建议使用 `m_hFile`，因为成员的含义取决于派生类。 `m_hFile` 成为一个公共成员，以便于支持类的非多态使用。

##  <a name="m_ptm"></a>CFile：： m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

##  <a name="open"></a>CFile：： Open

已重载。 `Open` 专用于默认 `CFile` 构造函数。

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

### <a name="parameters"></a>parameters

*lpszFileName*<br/>
包含所需文件的路径的字符串。 路径可以是相对路径、绝对路径或网络名称（UNC）。

*nOpenFlags*<br/>
定义文件的共享和访问模式的 UINT。 它指定打开文件时要执行的操作。 可以使用按位 "或" （ **&#124;** ）运算符组合选项。 需要一个访问权限和一个共享选项;`modeCreate` 模式和 `modeNoInherit` 模式是可选的。 有关模式选项的列表，请参阅[CFile](#cfile)构造函数。

*pError*<br/>
指向将接收失败操作的状态的现有文件异常对象的指针。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="return-value"></a>返回值

如果打开成功，则为非零值;否则为0。 仅当返回0时， *pError*参数才有意义。

### <a name="remarks"></a>备注

这两个 `Open` 函数是用于打开文件的 "安全" 方法，在这种情况下，失败是正常的、预期的情况。

尽管 `CFile` 构造函数在出现错误条件时引发异常，`Open` 对于错误条件返回 FALSE。 但 `Open` 仍可初始化[CFileException](../../mfc/reference/cfileexception-class.md)对象来描述错误。 如果未提供*pError*参数，或者如果为*pError*传递 NULL，`Open` 将返回 FALSE，并且不会引发 `CFileException`。 如果将指针传递到现有 `CFileException`，并且 `Open` 遇到错误，则该函数将用描述该错误的信息来填充它。 在这两种情况下，`Open` 不会引发异常。

下表描述了 `Open`可能的结果。

|`pError`|遇到错误|返回值|CFileException 内容|
|--------------|------------------------|------------------|----------------------------|
|Null|否|TRUE|不适用|
|指向 `CFileException` 的 ptr|否|TRUE|未更改|
|Null|是|FALSE|不适用|
|指向 `CFileException` 的 ptr|是|FALSE|初始化以描述错误|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>CFile：： operator 句柄

使用此运算符将 `CFile` 对象的句柄传递给需要 `HANDLE`的函数（例如[ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex)和[getfiletime 期间](/windows/win32/api/fileapi/nf-fileapi-getfiletime)）。

```
operator HANDLE() const;
```

##  <a name="read"></a>CFile：： Read

将数据从与 `CFile` 对象关联的文件读入缓冲区。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>parameters

*lpBuf*<br/>
指向用户提供的用于接收从文件中读取的数据的缓冲区的指针。

*nCount*<br/>
要从文件中读取的最大字节数。 对于文本模式文件，回车换行符对将作为单个字符进行计数。

### <a name="return-value"></a>返回值

传输到缓冲区的字节数。 对于所有 `CFile` 类，如果已到达文件末尾，则返回值可能小于*nCount* 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

有关其他示例，请参阅[CFile：： Open](#open)。

##  <a name="remove"></a>CFile：： Remove

此静态函数删除由路径指定的文件。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>parameters

*lpszFileName*<br/>
作为所需文件的路径的字符串。 路径可以是相对路径或绝对路径，并且可以包含网络名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

`Remove` 不会删除目录。

如果已打开连接的文件或无法删除文件，则 `Remove` 成员函数将引发异常。 此函数等效于 DEL 命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>CFile：： Rename

此静态函数会重命名指定的文件。

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>parameters

*lpszOldName*<br/>
旧路径。

*lpszNewName*<br/>
新的路径。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

不能重命名目录。 此函数等效于 REN 命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile：： Seek

重新定位打开文件中的文件指针。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>parameters

*lOff*<br/>
要将文件指针移动到的字节数。 正值将文件指针移动到文件末尾;负值将文件指针移动到文件的开头。

*n*<br/>
要查找的位置。 有关可能的值，请参阅备注部分。

### <a name="return-value"></a>返回值

如果方法成功，则为文件指针的位置;否则，返回值为 undefined，并引发指向 `CFileException` 异常的指针。

### <a name="remarks"></a>备注

下表列出了*n*参数的可能值。

|值|说明|
|-----------|-----------------|
|`CFile::begin`|从文件的开头进行查找。|
|`CFile::current`|从文件指针的当前位置进行查找。|
|`CFile::end`|从文件的末尾进行查找。|

打开文件时，文件指针将位于文件开头的0。

可以将文件指针设置为超出文件末尾的位置。 如果这样做，则在写入文件之前，文件的大小不会增加。

处理异常后，此方法的异常处理程序必须删除异常对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>CFile：： SeekToBegin

将文件指针的值设置为文件的开头。

```
void SeekToBegin();
```

### <a name="remarks"></a>备注

`SeekToBegin()` 等效于 `Seek( 0L, CFile::begin )`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>CFile：： SeekToEnd

将文件指针的值设置为文件的逻辑端。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>返回值

文件的长度（以字节为单位）。

### <a name="remarks"></a>备注

`SeekToEnd()` 等效于 `CFile::Seek( 0L, CFile::end )`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>CFile：： SetFilePath

调用此函数可指定文件的路径。 例如，如果在构造[CFile](../../mfc/reference/cfile-class.md)对象时文件路径不可用，则调用 `SetFilePath` 来提供该对象。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>parameters

*lpszNewName*<br/>
指向指定新路径的字符串的指针。

### <a name="remarks"></a>备注

> [!NOTE]
> `SetFilePath` 不会打开文件或创建文件;它只是将 `CFile` 对象与路径名称关联，然后可以使用该路径名称。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>CFile：： SetLength

调用此函数可更改文件的长度。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>parameters

*dwNewLen*<br/>
所需的文件长度（以字节为单位）。 此值可以大于或小于文件的当前长度。 文件将根据需要进行扩展或截断。

### <a name="remarks"></a>备注

> [!NOTE]
>  使用 `CMemFile`时，此函数可能引发 `CMemoryException` 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>CFile：： SetStatus

设置与此文件位置相关联的文件的状态。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>parameters

*lpszFileName*<br/>
作为所需文件的路径的字符串。 路径可以是相对路径或绝对路径，并且可以包含网络名称。

*status*<br/>
包含新状态信息的缓冲区。 调用 `GetStatus` 成员函数以 prefill 包含当前值的 `CFileStatus` 结构，然后根据需要进行更改。 如果值为0，则不更新相应的状态项。 有关 `CFileStatus` 结构的说明，请参阅[GetStatus](#getstatus)成员函数。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

若要设置时间，请修改 "*状态*" 的 "`m_mtime`" 字段。

当你对 `SetStatus` 进行调用以尝试仅更改文件的属性，并且文件状态结构的 `m_mtime` 成员为非零值时，属性也可能会受到影响（更改时间戳可能会对特性有副作用）。 如果只想更改文件的属性，请首先将文件状态结构的 `m_mtime` 成员设置为零，然后调用 `SetStatus`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>CFile：： UnlockRange

解锁打开文件中的某个范围的字节。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>parameters

*dwPos*<br/>
要解锁的字节范围起始处的字节偏移量。

*dwCount*<br/>
要解锁的范围中的字节数。

### <a name="remarks"></a>备注

有关详细信息，请参阅[LockRange](#lockrange)成员函数的说明。

> [!NOTE]
>  此函数不可用于 `CMemFile`派生的类。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile：： Write

将数据从缓冲区写入与 `CFile` 对象关联的文件。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>parameters

*lpBuf*<br/>
指向用户提供的缓冲区的指针，该缓冲区包含要写入到文件中的数据。

*nCount*<br/>
要从缓冲区传输的字节数。 对于文本模式文件，回车换行符对将作为单个字符进行计数。

### <a name="remarks"></a>备注

`Write` 引发异常来响应若干条件，包括磁盘-full 条件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

另请参阅[CFile：： CFile](#cfile)和[CFile：： Open](#open)的示例。

## <a name="see-also"></a>另请参阅

[MFC 示例 DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 类](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 类](../../mfc/reference/cmemfile-class.md)
