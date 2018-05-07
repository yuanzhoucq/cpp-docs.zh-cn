---
title: CCommandLineInfo 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43bd8f7b12eee847fd6b8784d21f4b565c7fc6a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo 类
辅助在应用程序启动时分析命令行。  
  
## <a name="syntax"></a>语法  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|构造默认`CCommandLineInfo`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCommandLineInfo::ParseParam](#parseparam)|重写此回调以分析单个参数。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|指示命令行`/Automation`找选项。|  
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|指示命令行`/Embedding`找选项。|  
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|指示是否应显示初始屏幕。|  
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|指示要处理的 shell 命令。|  
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|指示该驱动程序名称在 shell 命令为打印;否则为空。|  
|[CCommandLineInfo::m_strFileName](#m_strfilename)|指示要打开或打印的文件名称shell 命令是新建还是 DDE 空。|  
|[CCommandLineInfo::m_strPortName](#m_strportname)|指示端口名称 shell 命令是否打印受到保护。否则为空。|  
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|指示打印机名称 shell 命令是否打印受到保护。否则为空。|  
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|如果重新启动管理器重新启动应用程序，请重新启动管理器中指示的唯一的重新启动标识符。|  
  
## <a name="remarks"></a>备注  
 MFC 应用程序通常会创建此类中的本地实例[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)其应用程序对象的函数。 此对象然后传递给[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)，从而反复调用[ParseParam](#parseparam)以填充`CCommandLineInfo`对象。 `CCommandLineInfo`对象随后会传递给[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)来处理命令行自变量和标志。  
  
 你可以使用此对象将封装的以下命令行选项和参数：  
  
|命令行参数|执行命令|  
|----------------------------|----------------------|  
|*app*|新文件。|  
|*应用*filename|打开文件。|  
|*应用* `/p` filename|打印文件复制到默认打印机。|  
|*应用* `/pt` filename 打印机驱动程序端口|打印文件复制到指定的打印机。|  
|*应用程序* `/dde`|启动和 await DDE 命令。|  
|*应用程序* `/Automation`|OLE 自动化服务器启动。|  
|*应用程序* `/Embedding`|启动要编辑嵌入的 OLE 项。|  
|*应用程序* `/Register`<br /><br /> *应用程序* `/Regserver`|通知应用程序执行注册的任何任务。|  
|*应用程序* `/Unregister`<br /><br /> *应用程序* `/Unregserver`|通知应用程序执行任何取消注册任务。|  
  
 派生新类从`CCommandLineInfo`以处理其他标志和参数值。 重写[ParseParam](#parseparam)来处理新的标志。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo  
 此构造函数创建`CCommandLineInfo`具有默认值对象。  
  
```  
CCommandLineInfo();
```  
  
### <a name="remarks"></a>备注  
 默认值是以显示初始屏幕 ( `m_bShowSplash=TRUE`) 并在文件菜单上执行新的命令 ( `m_nShellCommand` **= NewFile**)。  
  
 应用程序框架调用[ParseParam](#parseparam)以填充此对象的数据成员。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]  
  
##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated  
 指示`/Automation`标志已找到命令行上。  
  
```  
BOOL m_bRunAutomated;  
```  
  
### <a name="remarks"></a>备注  
 如果`TRUE`，这意味着为 OLE 自动化服务器启动。  
  
##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded  
 指示`/Embedding`标志已找到命令行上。  
  
```  
BOOL m_bRunEmbedded;  
```  
  
### <a name="remarks"></a>备注  
 如果`TRUE`，这意味着启动以进行编辑嵌入的 OLE 项。  
  
##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash  
 指示应显示初始屏幕。  
  
```  
BOOL m_bShowSplash;  
```  
  
### <a name="remarks"></a>备注  
 如果`TRUE`，这意味着初始屏幕，此应用程序应显示在启动过程。 默认实现[ParseParam](#parseparam)将此数据成员设置为`TRUE`如果[m_nShellCommand](#m_nshellcommand)等同于`CCommandLineInfo::FileNew`。  
  
##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand  
 指示此实例的应用程序 shell 命令。  
  
```  
m_nShellCommand;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员的类型是以下中定义的枚举的类型`CCommandLineInfo`类。  
  
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
  
 有关这些值的简短说明，请参阅下面的列表。  
  
- `CCommandLineInfo::FileNew` 指示任何文件名已找到命令行上。  
  
- `CCommandLineInfo::FileOpen` 指示命令行上的文件名称找和以下标志的任何命令行上未找到： `/p`， `/pt`， `/dde`。  
  
- `CCommandLineInfo::FilePrint` 指示`/p`标志已找到命令行上。  
  
- `CCommandLineInfo::FilePrintTo` 指示`/pt`标志已找到命令行上。  
  
- `CCommandLineInfo::FileDDE` 指示`/dde`标志已找到命令行上。  
  
- `CCommandLineInfo::AppRegister` 指示`/Register`或`/Regserver`标志已找到命令行上，并要求应用程序以注册。  
  
- `CCommandLineInfo::AppUnregister` 指示`/Unregister`或`/Unregserver`向应用程序已请求取消注册。  
  
- `CCommandLineInfo::RestartByRestartManager` 指示重新启动管理器已重新启动应用程序。  
  
- `CCommandLineInfo::FileNothing` 关闭新的 MDI 子窗口在启动时显示。 按照设计，应用程序向导生成的 MDI 应用程序在启动时显示一个新的子窗口。 若要关闭此功能，应用程序可以使用`CCommandLineInfo::FileNothing`与 shell 命令时，它调用[ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)。 `ProcessShellCommand` 由调用`InitInstance( )`所有`CWinApp`派生类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]  
  
##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName  
 将第三个非标志参数的值存储在命令行上。  
  
```  
CString m_strDriverName;  
```  
  
### <a name="remarks"></a>备注  
 此参数通常是打印到 shell 命令的打印机驱动程序的名称。 默认实现[ParseParam](#parseparam)设置数据成员只有`/pt`标志已找到命令行上。  
  
##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName  
 在命令行上存储的第一个非标志参数的值。  
  
```  
CString m_strFileName;  
```  
  
### <a name="remarks"></a>备注  
 此参数通常是文件的要打开的名称。  
  
##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName  
 将第四个非标志参数的值存储在命令行上。  
  
```  
CString m_strPortName;  
```  
  
### <a name="remarks"></a>备注  
 此参数通常是打印到 shell 命令的打印机端口的名称。 默认实现[ParseParam](#parseparam)设置数据成员只有`/pt`标志已找到命令行上。  
  
##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName  
 将第二个非标志参数的值存储在命令行上。  
  
```  
CString m_strPrinterName;  
```  
  
### <a name="remarks"></a>备注  
 此参数通常是打印机的打印到 shell 命令的名称。 默认实现[ParseParam](#parseparam)设置数据成员只有`/pt`标志已找到命令行上。  
  
##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier  
 唯一，则将重新启动命令行上的标识符。  
  
```  
CString m_strRestartIdentifier;  
```  
  
### <a name="remarks"></a>备注  
 重新启动标识符是唯一的应用程序的每个实例。  
  
 如果重新启动管理器退出应用程序，并且配置为重新启动它，重新启动管理器执行的重新启动标识符在命令行中的可选参数的形式应用程序。 当重新启动管理器使用的重启标识符时，应用程序可以重新打开以前打开的文档和恢复自动保存文件。  
  
##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam  
 框架调用此函数可分析/解释从命令行的单个参数。 第二个版本与前者区别仅在 Unicode 项目中。  
  
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
 `pszParam`  
 参数或标志。  
  
 *bFlag*  
 指示是否`pszParam`参数或标志。  
  
 `bLast`  
 指示这是最后一个参数或命令行上的标志。  
  
### <a name="remarks"></a>备注  
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)调用`ParseParam`一次对于每个参数或命令行上的标志，将自变量传递到`pszParam`。 如果参数的第一个字符是**-**' **/**，它会被删除和*bFlag*设置为`TRUE`。 在分析的最后一个参数时,`bLast`设置为`TRUE`。  
  
 此函数的默认实现可识别以下标志： `/p`， `/pt`， `/dde`， `/Automation`，和`/Embedding`下, 表中所示：  
  
|命令行参数|执行命令|  
|----------------------------|----------------------|  
|*app*|新文件。|  
|*应用*filename|打开文件。|  
|*应用* `/p` filename|打印文件复制到默认打印机。|  
|*应用* `/pt` filename 打印机驱动程序端口|打印文件复制到指定的打印机。|  
|*应用程序* `/dde`|启动和 await DDE 命令。|  
|*应用程序* `/Automation`|OLE 自动化服务器启动。|  
|*应用程序* `/Embedding`|启动要编辑嵌入的 OLE 项。|  
|*应用程序* `/Register`<br /><br /> *应用程序* `/Regserver`|通知应用程序执行注册的任何任务。|  
|*应用程序* `/Unregister`<br /><br /> *应用程序* `/Unregserver`|通知应用程序执行任何取消注册任务。|  
  
 此信息存储在[m_bRunAutomated](#m_brunautomated)， [m_bRunEmbedded](#m_brunembedded)，和[m_nShellCommand](#m_nshellcommand)。 标志标记通过以下任一方法正斜杠**/**'或连字符' **-**。  
  
 默认实现将放置到的第一个非标志参数[m_strFileName](#m_strfilename)。 情况下`/pt`标志，默认实现将第二、 三和第四个非标志参数转换[m_strPrinterName](#m_strprintername)， [m_strDriverName](#m_strdrivername)，和[m_strPortName](#m_strportname)分别。  
  
 默认实现还设置[m_bShowSplash](#m_bshowsplash)到`TRUE`仅在新的文件的情况下。 如果是新文件，用户已执行涉及应用程序本身的操作。 在任何其他情况下，包括打开现有文件使用命令行程序，用户执行任何操作直接涉及文件。 以文档为中心的角度来看，在不需要宣布启动应用程序初始屏幕。  
  
 重写此函数在处理其他标志和参数值在派生类中。  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)   
 [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

