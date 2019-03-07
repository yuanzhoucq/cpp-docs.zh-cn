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
ms.openlocfilehash: f287b04b32b7bc45342ac7248fbe986a3dcf959e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289862"
---
# <a name="cfile-class"></a>CFile 类

Microsoft 基础类文件类的基类。

## <a name="syntax"></a>语法

```
class CFile : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFile::CFile](#cfile)|构造`CFile`从路径或文件句柄的对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFile::Abort](#abort)|关闭正在忽略所有警告和错误的文件。|
|[CFile::Close](#close)|关闭文件并删除该对象。|
|[CFile::Duplicate](#duplicate)|构造一个基于此文件的复制对象。|
|[CFile::Flush](#flush)|刷新所有数据尚未被写入。|
|[CFile::GetFileName](#getfilename)|检索所选文件的文件名。|
|[CFile::GetFilePath](#getfilepath)|检索所选文件的完整文件路径。|
|[CFile::GetFileTitle](#getfiletitle)|检索所选文件的标题。|
|[CFile::GetLength](#getlength)|检索文件的长度。|
|[CFile::GetPosition](#getposition)|检索当前的文件指针。|
|[CFile::GetStatus](#getstatus)|检索状态的打开的文件，或在静态版本中，检索指定的文件 （静态、 虚拟函数） 的状态。|
|[CFile::LockRange](#lockrange)|锁定文件中的字节的范围。|
|[CFile::Open](#open)|安全地打开文件的错误测试选项。|
|[CFile::Read](#read)|从当前文件位置的文件读取 （无缓冲） 数据。|
|[CFile::Remove](#remove)|删除指定的文件 （静态函数）。|
|[CFile::Rename](#rename)|重命名指定的文件 （静态函数）。|
|[CFile::Seek](#seek)|将当前文件指针定位。|
|[CFile::SeekToBegin](#seektobegin)|将当前文件指针置于文件的开头。|
|[CFile::SeekToEnd](#seektoend)|在文件末尾将当前文件指针定位。|
|[CFile::SetFilePath](#setfilepath)|设置所选文件的完整文件路径。|
|[CFile::SetLength](#setlength)|更改文件的长度。|
|[CFile::SetStatus](#setstatus)|设置指定的文件 （静态、 虚拟函数） 的状态。|
|[CFile::UnlockRange](#unlockrange)|解除锁定文件中的字节的范围。|
|[CFile::Write](#write)|（无缓冲） 将数据写入到当前文件位置的文件中。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CFile::operator 句柄](#operator_handle)|句柄`CFile`对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|确定如果`CFile`对象具有有效的句柄。|
|[CFile::m_hFile](#m_hfile)|通常包含操作系统文件句柄。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|指向`CAtlTransactionManager`对象。|

## <a name="remarks"></a>备注

它直接提供未缓冲，二进制磁盘输入/输出服务，并间接支持文本文件和通过其派生类的内存文件。 `CFile` 结合工作`CArchive`类，以支持 Microsoft 基础类对象的序列化。

此类与它的派生的类之间的分层关系允许你通过多态的所有文件对象上运行的程序`CFile`接口。 内存文件，例如，类似于磁盘文件的行为。

使用`CFile`通用磁盘 I/O 及其派生类。 使用`ofstream`或用于格式化文本发送到磁盘文件的其他 Microsoft iostream 类。

通常情况下上自动, 打开磁盘文件`CFile`构造和析构上已关闭。 静态成员函数允许您询问而无需打开该文件的文件的状态。

有关使用的详细信息`CFile`，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)并[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="abort"></a>  CFile::Abort

关闭与此对象关联的文件，并使该文件进行读取或写入不可用。

```
virtual void Abort();
```

### <a name="remarks"></a>备注

如果您未销毁对象之前关闭该文件，析构函数将关闭它。

在处理异常时,`CFile::Abort`不同于`CFile::Close`在两个重要方面。 首先，`Abort`函数将不引发异常，故障因为故障，将忽略`Abort`。 第二个，`Abort`将不会**ASSERT**如果文件未打开或以前已关闭。

如果您使用了**新**分配`CFile`对象在堆上，则必须关闭文件后删除它。 `Abort` 设置`m_hFile`到`CFile::hFileNull`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>  CFile::CFile

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

*lpszFileName*<br/>
要附加到 `CFile` 对象的文件的相对路径或完整路径。

*nOpenFlags*<br/>
指定文件的文件访问选项的按位组合 (OR)。 有关可能的选项，请参阅“备注”部分。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

以下五个表列出了可能的选项*nOpenFlags*参数。

仅选择下列文件访问模式选项之一。 默认文件访问模式为 `CFile::modeRead`，该模式为只读模式。

|值|描述|
|-----------|-----------------|
|`CFile::modeRead`|只请求读取访问权限。|
|`CFile::modeWrite`|只请求写入访问权限。|
|`CFile::modeReadWrite`|请求读写访问权限。|

选择以下字符模式选项之一。

|值|描述|
|-----------|-----------------|
|`CFile::typeBinary`|设置二元模式（仅在派生类中使用）。|
|`CFile::typeText`|设置文本模式进行特殊处理，回车-换行对 （在仅派生类中使用）。|
|`CFile::typeUnicode`|设置 Unicode 模式（仅在派生类中使用）。 当应用程序在 Unicode 配置中生成时，文本将以 Unicode 格式写入文件中。 不会将 BOM 写入该文件中。|

仅选择下列文件共享模式选项之一。 默认文件共享模式为 `CFile::shareExclusive`，该模式是独占模式。

|值|描述|
|-----------|-----------------|
|`CFile::shareDenyNone`|没有任何共享限制。|
|`CFile::shareDenyRead`|拒绝向所有其他用户提供读取访问权限。|
|`CFile::shareDenyWrite`|拒绝向所有其他用户提供写入访问权限。|
|`CFile::shareExclusive`|拒绝向所有其他用户提供读写访问权限。|

选择下面的第一个（或全选）文件创建模式选项。 默认创建模式为 `CFile::modeNoTruncate`，该模式当前处于打开状态。

|值|描述|
|-----------|-----------------|
|`CFile::modeCreate`|如果文件不存在，请创建一个新文件。 如果该文件已存在，它是被覆盖，并最初设置为长度为零。|
|`CFile::modeNoTruncate`|若文件不存在，则创建新文件；否则，如果该文件已存在，则将其附加到 `CFile` 对象。|

按照描述选择以下文件缓存选项。 默认情况下，系统将使用通用的缓存方案，该方案不可用作选项。

|值|描述|
|-----------|-----------------|
|`CFile::osNoBuffer`|系统没有为文件使用中间缓存。 此选项取消以下 2 个选项。|
|`CFile::osRandomAccess`|文件缓存针对随机访问进行了优化。 不要使用此选项和顺序扫描选项。|
|`CFile::osSequentialScan`|文件缓存针对顺序访问进行了优化。 不要使用此选项和随机访问选项。|
|`CFile::osWriteThrough`|立即执行写入操作。|

选择下列安全选项以防止继承文件句柄。 默认情况下，所有新的子进程都可以使用文件句柄。

|值|描述|
|-----------|-----------------|
|`CFile::modeNoInherit`|阻止任何子进程使用文件句柄。|

默认构造函数将初始化成员，但不会将文件附加到 `CFile` 对象。 在使用此构造函数之后, 使用[CFile::Open](#open)方法来打开文件并将其附加到`CFile`对象。

带有一个参数的构造函数将初始化成员，并且将现有文件附加到 `CFile` 对象。

带有两个参数的构造函数将初始化成员并尝试打开指定文件。 若此构造函数成功打开指定文件，则该文件将附加到 `CFile` 对象；否则，此构造函数将引发指向 `CInvalidArgException` 对象的指针。 有关如何处理异常的详细信息，请参阅[异常](../../mfc/exception-handling-in-mfc.md)。

如果 `CFile` 对象成功打开指定文件，则它将在 `CFile` 对象被销毁时自动关闭该文件；否则，你必须在不再将其附加到 `CFile` 对象之后显式关闭该文件。

### <a name="example"></a>示例

下面的代码演示如何使用 `CFile`。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>  CFile::Close

关闭与此对象关联的文件，并使该文件进行读取或写入不可用。

```
virtual void Close();
```

### <a name="remarks"></a>备注

如果您未销毁对象之前关闭该文件，析构函数将关闭它。

如果您使用了**新**分配`CFile`对象在堆上，则必须关闭文件后删除它。 `Close` 设置`m_hFile`到`CFile::hFileNull`。

### <a name="example"></a>示例

有关示例，请参阅[CFile::CFile](#cfile)。

##  <a name="duplicate"></a>  CFile::Duplicate

构造重复`CFile`给定文件的对象。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>返回值

指向一个重复的`CFile`对象。

### <a name="remarks"></a>备注

这相当于 C 运行时函数`_dup`。

##  <a name="flush"></a>  CFile::Flush

强制在要写入到文件的文件缓冲区中剩余的任何数据。

```
virtual void Flush();
```

### <a name="remarks"></a>备注

利用`Flush`不能保证刷新`CArchive`缓冲区。 如果使用的存档，调用[CArchive::Flush](../../mfc/reference/carchive-class.md#flush)第一个。

### <a name="example"></a>示例

有关示例，请参阅[CFile::SetFilePath](#setfilepath)。

##  <a name="getfilename"></a>  CFile::GetFileName

调用此成员函数以检索指定文件的名称。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>返回值

文件的名称。

### <a name="remarks"></a>备注

例如，当您调用`GetFileName`以生成有关文件用户显示消息`c:\windows\write\myfile.wri`，文件名， `myfile.wri`，则返回。

若要返回整个文件的路径，包括名称、 调用[GetFilePath](#getfilepath)。 若要返回文件的标题 ( `myfile`)，调用[GetFileTitle](#getfiletitle)。

### <a name="example"></a>示例

此代码段打开系统。在 WINDOWS 目录中的 INI 文件。 如果找到，该示例将打印出的名称和路径和标题，如输出所示：

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

调用此成员函数以检索指定的文件的完整路径。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>返回值

指定文件的完整路径。

### <a name="remarks"></a>备注

例如，当您调用`GetFilePath`以生成有关文件用户显示消息`c:\windows\write\myfile.wri`的文件路径， `c:\windows\write\myfile.wri`，则返回。

若要返回只是文件的名称 (`myfile.wri`)，调用[GetFileName](#getfilename)。 若要返回文件的标题 (`myfile`)，调用[GetFileTitle](#getfiletitle)。

### <a name="example"></a>示例

有关示例，请参阅[GetFileName](#getfilename)。

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

调用此成员函数以检索该文件的文件标题 （显示名称）。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>返回值

基础文件的标题。

### <a name="remarks"></a>备注

此方法调用[GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea)检索文件的标题。 如果成功，该方法将返回系统将使用要向用户显示的文件的名称的字符串。 否则，该方法会调用[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)检索基础文件的文件名称 （包括文件扩展名）。 因此，文件扩展名将始终是字符串中未包含返回的文件标题。 有关详细信息，请参阅[GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea)并[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) Windows SDK 中。

若要返回整个文件的路径，包括名称、 调用[GetFilePath](#getfilepath)。 若要返回只是文件的名称，请调用[GetFileName](#getfilename)。

### <a name="example"></a>示例

有关示例，请参阅[GetFileName](#getfilename)。

##  <a name="getlength"></a>  CFile::GetLength

获取以字节为单位的文件的当前逻辑长度。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>返回值

文件的长度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

获取文件指针，它可以对后续调用中使用的当前值`Seek`。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>返回值

文件指针中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>  CFile::GetStatus

此方法检索与相关的状态信息给定`CFile`对象实例或给定的文件路径。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*rStatus*<br/>
对用户提供的引用`CFileStatus`结构，它将接收的状态信息。 `CFileStatus`结构具有以下字段：

- `CTime m_ctime` 日期和时间已创建了文件中。

- `CTime m_mtime` 日期和该文件的上次修改的时间。

- `CTime m_atime` 日期和时间上一次访问该文件进行读取。

- `ULONGLONG m_size` 以字节为单位，报告的 DIR 命令文件的逻辑大小。

- `BYTE m_attribute` 文件属性字节。

- `char m_szFullName[_MAX_PATH]` 在 Windows 字符集中的绝对文件名。

*lpszFileName*<br/>
中的 Windows 字符的字符串，它是设置所需的文件的路径。 路径可以是相对或绝对的也可以包含网络路径名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="return-value"></a>返回值

如果成功地获取指定的文件的状态信息; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

非静态新版`GetStatus`打开的文件与相关联的状态信息中检索给定`CFile`对象。  静态版本`GetStatus`从给定的文件路径获取文件状态，而无需实际打开该文件。 这是用于测试的文件存在和访问权限。

`m_attribute`的成员`CFileStatus`结构引用的文件属性集。 `CFile`类提供了**属性**枚举类型，因此可以种指定文件属性：

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

##  <a name="hfilenull"></a>  CFile::hFileNull

确定是否存在有效的文件句柄`CFile`对象。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>备注

使用此常量来确定如果`CFile`对象具有有效的文件句柄。

下面的示例演示了此操作：

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

锁定一的系列字节中打开的文件，如果该文件已被锁定，则引发异常。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>参数

*dwPos*<br/>
要锁定的字节范围的开始的字节偏移量。

*dwCount*<br/>
要锁定的范围中的字节数。

### <a name="remarks"></a>备注

锁定文件中的字节将阻止其他进程访问这些字节。 可锁定多个区域文件，但允许使用任何重叠区域。

如果解除锁定区域，使用`UnlockRange`成员函数的字节范围必须对应完全以前锁定的区域。 `LockRange`函数不会合并相邻区域; 如果有两种锁定的区域相邻，必须单独解锁每个区域。

> [!NOTE]
>  此函数不可用于`CMemFile`-派生的类。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

包含打开的文件的操作系统文件句柄。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>备注

`m_hFile` 是类型为 UINT 的公共变量。 它包含`CFile::hFileNull`（独立于操作系统的空文件指标） 如果尚未分配句柄。

使用`m_hFile`不建议，因为该成员的含义取决于派生的类。 `m_hFile` 将成为公共成员，为方便起见，在支持非多态类的使用。

##  <a name="m_ptm"></a>  CFile::m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

##  <a name="open"></a>  CFile::Open

已重载。 `Open` 设计用于默认`CFile`构造函数。

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

*lpszFileName*<br/>
一个字符串，是所需的文件的路径。 路径可以是相对、 绝对路径或网络名称 (UNC)。

*nOpenFlags*<br/>
UINT，用于定义文件的共享和访问模式。 它指定打开文件时采取的操作。 可以通过使用按位 OR 组合选项 ( **&#124;** ) 运算符。 一个访问权限和一个共享选项是必需的;`modeCreate`和`modeNoInherit`模式是可选的。 请参阅[CFile](#cfile)构造函数模式选项的列表。

*pError*<br/>
指向将接收失败的操作的状态的现有文件异常对象的指针。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="return-value"></a>返回值

如果打开成功，则非零值否则为 0。 *PError*参数是返回 0 时，才有意义。

### <a name="remarks"></a>备注

两个函数窗体"安全"方法来打开一个文件，其中失败是正常的预期条件。

虽然`CFile`构造函数将引发异常错误条件中`Open`将对错误条件返回 FALSE。 `Open` 仍可以初始化[CFileException](../../mfc/reference/cfileexception-class.md)对象，用于描述该错误，但是。 如果未提供*pError*参数，或如果您为传递 NULL *pError*，`Open`将返回 FALSE，因此不会引发`CFileException`。 如果将指针传递到的现有`CFileException`，和`Open`遇到的错误，该函数将填充描述该错误的信息。 中都不写将`Open`引发异常。

下表描述了可能的结果`Open`。

|`pError`|遇到错误|返回值|CFileException 内容|
|--------------|------------------------|------------------|----------------------------|
|NULL|否|true|n/a|
|到 ptr `CFileException`|否|true|未更改|
|NULL|是|false|n/a|
|到 ptr `CFileException`|是|false|初始化来描述错误|

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>  CFile::operator 句柄

使用此运算符传递的句柄`CFile`对象传递给函数如[ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex)并[GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime)的预期`HANDLE`。

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

将数据读入的缓冲区与关联的文件从`CFile`对象。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向将接收从文件中读取的数据的用户提供的缓冲区的指针。

*nCount*<br/>
要从文件读取的字节数目上限。 对于文本模式下的文件，回车-换行对计为单个字符。

### <a name="return-value"></a>返回值

传输到缓冲区的字节数。 请注意，对于所有`CFile`类，则返回值可能小于*nCount*如果已达到文件结尾。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

另一个示例，请参阅[CFile::Open](#open)。

##  <a name="remove"></a>  CFile::Remove

此静态函数删除由路径指定的文件。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpszFileName*<br/>
一个字符串，是所需的文件的路径。 路径可以是相对或绝对的并且可以包含网络名称。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

它不会删除一个目录。

`Remove`成员函数将引发异常，如果已连接的文件处于打开状态，或不能删除该文件。 这相当于 DEL 命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>  CFile::Rename

此静态函数重命名指定的文件。

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpszOldName*<br/>
旧的路径。

*lpszNewName*<br/>
新的路径。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

不能重命名目录。 这相当于 REN 命令。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>  CFile::Seek

文件指针重新定位在打开的文件中。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>参数

*lOff*<br/>
要将文件指针移动的字节数。 值为正移动文件; 末尾的指针负值将文件指针移向文件的开始。

*nFrom*<br/>
要从定位的位置。 请参阅备注部分中有关可能的值。

### <a name="return-value"></a>返回值

如果此方法已成功，则文件指针的位置否则，返回值是不确定和一个指向`CFileException`引发异常。

### <a name="remarks"></a>备注

下表列出了可能值*nFrom*参数。

|值|描述|
|-----------|-----------------|
|`CFile::begin`|从文件开头向搜索。|
|`CFile::current`|从文件指针的当前位置向搜索。|
|`CFile::end`|从文件末尾进行查找。|

当打开文件时，文件指针位于保持为 0，文件开头。

您可以将文件指针设置到超出文件末尾的位置。 如果这样做，文件的大小不会增加之前写入到文件。

处理异常后，此方法的异常处理程序必须删除异常对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>  CFile::SeekToBegin

将文件指针的值设置为该文件的开头。

```
void SeekToBegin();
```

### <a name="remarks"></a>备注

`SeekToBegin()` 与 `Seek( 0L, CFile::begin )` 相等。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>  CFile::SeekToEnd

将文件指针的值设置为的逻辑文件结尾。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>返回值

文件的长度（以字节为单位）。

### <a name="remarks"></a>备注

`SeekToEnd()` 与 `CFile::Seek( 0L, CFile::end )` 相等。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>  CFile::SetFilePath

调用此函数可指定在文件的路径例如，如果文件的路径不可用[CFile](../../mfc/reference/cfile-class.md)构造对象，请调用`SetFilePath`提供它。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>参数

*lpszNewName*<br/>
指定新路径的字符串指针。

### <a name="remarks"></a>备注

> [!NOTE]
> `SetFilePath` 不会打开该文件或创建该文件;它只需将相关联`CFile`路径名称，然后，可以使用与对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

调用此函数可更改文件的长度。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>参数

*dwNewLen*<br/>
所需的文件以字节为单位的长度。 此值可以是大于或小于该文件的当前长度。 将扩展或截断根据该文件。

### <a name="remarks"></a>备注

> [!NOTE]
>  与`CMemFile`，此函数可能会引发`CMemoryException`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>  CFile::SetStatus

设置与此文件位置相关联的文件的状态。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>参数

*lpszFileName*<br/>
一个字符串，是所需的文件的路径。 路径可以是相对或绝对的并且可以包含网络名称。

*status*<br/>
包含新的状态信息的缓冲区。 调用`GetStatus`成员函数，以预填充`CFileStatus`结构的当前值，然后根据需要进行更改。 如果值为 0，则不更新相应的状态项。 请参阅[GetStatus](#getstatus)成员函数的说明`CFileStatus`结构。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

若要设置的时间，修改`m_mtime`字段*状态*。

请注意，当您调用`SetStatus`在尝试更改文件属性和`m_mtime`文件状态结构中的成员为非零值、 属性可能也会受到影响 （更改的时间戳可能会对产生负面影响属性）。 如果你想要仅更改文件的属性，首先设置`m_mtime`的文件状态结构的成员为零，然后再调用`SetStatus`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>  CFile::UnlockRange

解除锁定打开的文件中的字节的范围。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>参数

*dwPos*<br/>
要解锁的字节范围的开始的字节偏移量。

*dwCount*<br/>
要解锁的范围中的字节数。

### <a name="remarks"></a>备注

请参阅的说明[LockRange](#lockrange)成员函数的详细信息。

> [!NOTE]
>  此函数不可用于`CMemFile`-派生的类。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>  CFile::Write

将数据从缓冲区写入到与关联的文件`CFile`对象。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向包含要写入到文件的数据的用户提供的缓冲区的指针。

*nCount*<br/>
要从缓冲区传输的字节数。 对于文本模式下的文件，回车-换行对计为单个字符。

### <a name="remarks"></a>备注

`Write` 到多个条件，包括磁盘已满条件的响应，则会引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

此外，请参阅有关[CFile::CFile](#cfile)并[CFile::Open](#open)。

## <a name="see-also"></a>请参阅

[MFC 示例 DRAWCLI](../../visual-cpp-samples.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile 类](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile 类](../../mfc/reference/cmemfile-class.md)
