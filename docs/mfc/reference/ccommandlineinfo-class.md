---
title: CCommandLineInfo 类
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369459"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo 类

辅助在应用程序启动时分析命令行。

## <a name="syntax"></a>语法

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCommandLine信息：CCommandLineinfo](#ccommandlineinfo)|构造默认`CCommandLineInfo`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|重写此回调以分析单个参数。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCommandLine信息：m_bRunAutomated](#m_brunautomated)|指示找到命令行`/Automation`选项。|
|[CCommandLine信息：：m_bRunEmbedded](#m_brunembedded)|指示找到命令行`/Embedding`选项。|
|[CCommandLine信息：m_bShowSplash](#m_bshowsplash)|指示是否应显示初始屏幕。|
|[CCommandLine信息：m_nShellCommand](#m_nshellcommand)|指示要处理的 shell 命令。|
|[CCommandLine信息：：m_strDriverName](#m_strdrivername)|如果 shell 命令为"打印到"，则指示驱动程序名称;否则为空。|
|[CCommandLine信息：：m_strFileName](#m_strfilename)|指示要打开或打印的文件名;如果 shell 命令为"新建"或"DDE"，则为空。|
|[CCommandLine信息：：m_strPortName](#m_strportname)|如果 shell 命令是"打印到"，则指示端口名称;否则为空。|
|[CCommandLine信息：m_strPrinterName](#m_strprintername)|如果 shell 命令为"打印到"，则指示打印机名称;否则为空。|
|[CCommandLine信息：m_strRestartIdentifier](#m_strrestartidentifier)|指示重新启动管理器重新启动应用程序时重新启动管理器的唯一重新启动标识符。|

## <a name="remarks"></a>备注

MFC 应用程序通常会在其应用程序对象的[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)函数中创建此类的本地实例。 然后，此对象将传递给[CWinApp：:ParseCommandLine，该命令线](../../mfc/reference/cwinapp-class.md#parsecommandline)重复调用[ParseParam](#parseparam)来填充`CCommandLineInfo`该对象。 然后`CCommandLineInfo`，该对象将传递给[CWinApp：:ProcessShellCommand，](../../mfc/reference/cwinapp-class.md#processshellcommand)以处理命令行参数和标志。

可以使用此对象封装以下命令行选项和参数：

|命令行参数|命令已执行|
|----------------------------|----------------------|
|*应用*|新文件。|
|*应用*文件名|打开文件。|
|*应用*`/p`文件名|将文件打印到默认打印机。|
|*应用程序*`/pt`文件名打印机驱动程序端口|将文件打印到指定的打印机。|
|*应用* `/dde`|启动并等待 DDE 命令。|
|*应用* `/Automation`|启动为 OLE 自动化服务器。|
|*应用* `/Embedding`|启动以编辑嵌入的 OLE 项目。|
|*应用* `/Register`<br /><br /> *应用* `/Regserver`|通知应用程序执行任何注册任务。|
|*应用* `/Unregister`<br /><br /> *应用* `/Unregserver`|通知应用程序执行任何取消注册任务。|

派生新`CCommandLineInfo`类以处理其他标志和参数值。 覆盖[ParseParam](#parseparam)以处理新标志。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLine信息：CCommandLineinfo

此构造函数创建具有`CCommandLineInfo`默认值的对象。

```
CCommandLineInfo();
```

### <a name="remarks"></a>备注

默认值是显示初始屏幕 （ `m_bShowSplash=TRUE`）， 并在"文件" 菜单 （ `m_nShellCommand` **#NewFile**） 上执行"新建"命令。

应用程序框架调用[ParseParam](#parseparam)来填充此对象的数据成员。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLine信息：m_bRunAutomated

指示在`/Automation`命令行上找到标志。

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>备注

如果为 TRUE，则意味着启动为 OLE 自动化服务器。

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLine信息：：m_bRunEmbedded

指示在`/Embedding`命令行上找到标志。

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>备注

如果为 TRUE，则意味着启动以编辑嵌入的 OLE 项目。

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLine信息：m_bShowSplash

指示应显示初始屏幕。

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>备注

如果为 TRUE，则意味着此应用程序的初始屏幕应在启动期间显示。 如果[m_nShellCommand](#m_nshellcommand)等于`CCommandLineInfo::FileNew`，[则 ParseParam](#parseparam)的默认实现将此数据成员设置为 TRUE。

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLine信息：m_nShellCommand

指示应用程序此实例的 shell 命令。

```
m_nShellCommand;
```

### <a name="remarks"></a>备注

此数据成员的类型为以下枚举类型，该类型在类中`CCommandLineInfo`定义。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

有关这些值的简要说明，请参阅以下列表。

- `CCommandLineInfo::FileNew`指示在命令行上未找到文件名。

- `CCommandLineInfo::FileOpen`指示在命令行上找到文件名，并且在命令行上未找到以下标志： `/p`， `/pt` `/dde`。

- `CCommandLineInfo::FilePrint`指示在`/p`命令行上找到标志。

- `CCommandLineInfo::FilePrintTo`指示在`/pt`命令行上找到标志。

- `CCommandLineInfo::FileDDE`指示在`/dde`命令行上找到标志。

- `CCommandLineInfo::AppRegister`指示在`/Register`命令行`/Regserver`上找到 或 标志，并要求应用程序注册。

- `CCommandLineInfo::AppUnregister`指示已要求`/Unregister``/Unregserver`或 应用程序取消注册。

- `CCommandLineInfo::RestartByRestartManager`指示重新启动管理器重新启动应用程序。

- `CCommandLineInfo::FileNothing`在启动时关闭新 MDI 子窗口的显示。 根据设计，应用程序向导生成的 MDI 应用程序在启动时显示一个新的子窗口。 要关闭此功能，应用程序在调用`CCommandLineInfo::FileNothing`[ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)时可以使用它作为 shell 命令。 `ProcessShellCommand`由 所有`CWinApp`派生`InitInstance( )`类的 调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLine信息：：m_strDriverName

将第三个非标志参数的值存储在命令行上。

```
CString m_strDriverName;
```

### <a name="remarks"></a>备注

此参数通常是打印到 shell 命令的打印机驱动程序的名称。 仅当在命令行上找到标志时[，ParseParam](#parseparam)`/pt`的默认实现才会设置此数据成员。

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLine信息：：m_strFileName

将第一个非标志参数的值存储在命令行上。

```
CString m_strFileName;
```

### <a name="remarks"></a>备注

此参数通常是要打开的文件的名称。

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLine信息：：m_strPortName

将第四个非标志参数的值存储在命令行上。

```
CString m_strPortName;
```

### <a name="remarks"></a>备注

此参数通常是打印到 shell 命令的打印机端口的名称。 仅当在命令行上找到标志时[，ParseParam](#parseparam)`/pt`的默认实现才会设置此数据成员。

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLine信息：m_strPrinterName

将第二个非标志参数的值存储在命令行上。

```
CString m_strPrinterName;
```

### <a name="remarks"></a>备注

此参数通常是打印到 shell 命令的打印机名称。 仅当在命令行上找到标志时[，ParseParam](#parseparam)`/pt`的默认实现才会设置此数据成员。

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLine信息：m_strRestartIdentifier

命令行上的唯一重新启动标识符。

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>备注

重新启动标识符对于应用程序的每个实例都是唯一的。

如果重新启动管理器退出应用程序并配置为重新启动应用程序，重新启动管理器将从命令行执行应用程序，并将重新启动标识符作为可选参数。 当重新启动管理器使用重新启动标识符时，应用程序可以重新打开以前打开的文档并恢复自动保存的文件。

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLine信息：:P

框架调用此函数来分析/解释命令行中的单个参数。 第二个版本与 Unicode 项目中的第一个版本不同。

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>参数

*pszParam*<br/>
参数或标志。

*bFlag*<br/>
指示*pszParam*是参数还是标志。

*爆炸*<br/>
指示这是命令行上的最后一个参数或标志。

### <a name="remarks"></a>备注

[CWinApp：:ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)为`ParseParam`命令行中的每个参数或标志调用一次，将参数传递给*pszParam*。 如果参数的第一个字符是''**-** 或''，**/** 则删除它并将*bFlag*设置为 TRUE。 分析最终参数时 *，bLast*设置为 TRUE。

此函数的默认实现可识别以下`/p`标志： 、 `/pt` `/dde`、 `/Automation`、 和`/Embedding`， 如下表所示：

|命令行参数|命令已执行|
|----------------------------|----------------------|
|*应用*|新文件。|
|*应用*文件名|打开文件。|
|*应用*`/p`文件名|将文件打印到默认打印机。|
|*应用程序*`/pt`文件名打印机驱动程序端口|将文件打印到指定的打印机。|
|*应用* `/dde`|启动并等待 DDE 命令。|
|*应用* `/Automation`|启动为 OLE 自动化服务器。|
|*应用* `/Embedding`|启动以编辑嵌入的 OLE 项目。|
|*应用* `/Register`<br /><br /> *应用* `/Regserver`|通知应用程序执行任何注册任务。|
|*应用* `/Unregister`<br /><br /> *应用* `/Unregserver`|通知应用程序执行任何取消注册任务。|

此信息存储在[m_bRunAutomated、m_bRunEmbedded](#m_brunautomated)和[m_bRunEmbedded](#m_brunembedded)[m_nShellCommand](#m_nshellcommand)中。 标志用前斜杠'**/** 或连字符'标记。 **-**

默认实现将第一个非标志参数放入[m_strFileName](#m_strfilename)。 在`/pt`标志的情况下，默认实现将第二个、第三个和第四个非标志参数分别放入[m_strPrinterName、m_strDriverName](#m_strprintername)和[m_strDriverName](#m_strdrivername)[m_strPortName。](#m_strportname)

默认实现还仅在新文件的情况下[将m_bShowSplash](#m_bshowsplash)设置为 TRUE。 在新文件的情况下，用户已执行涉及应用程序本身的操作。 在任何其他情况下，包括使用 shell 打开现有文件，用户操作将直接涉及该文件。 在以文档为中心的立场中，初始屏幕不需要宣布应用程序启动。

重写派生类中的此函数以处理其他标志和参数值。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp：:P](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp：:P罗塞斯舍尔命令](../../mfc/reference/cwinapp-class.md#processshellcommand)
