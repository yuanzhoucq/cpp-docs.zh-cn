---
title: /CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码）
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 5e4a5c86e53d74c8b704ee3780991d496fc1802a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273581"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码）

**/CLRSUPPORTLASTERROR**，即在默认情况下，保留通过 P/Invoke 机制，以便您可以从代码调用 DLL 中的本机函数调用的函数的最后一个错误代码编译 **/clr**。

## <a name="syntax"></a>语法

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>备注

保留最后一个错误代码表示性能降低。  如果不希望产生的保留的最后一个错误代码的性能影响，链接使用 **/CLRSUPPORTLASTERROR:NO**。

您可以通过链接性能影响降至最低 **/CLRSUPPORTLASTERROR:SYSTEMDLL**，其中仅保留系统 Dll 中函数的最后一个错误代码。  系统 DLL 定义为以下值之一：

|||||
|-|-|-|-|
|ACLUI.DLL|ACTIVEDS。DLL|ADPTIF.DLL|ADVAPI32.DLL|
|ASYCFILT.DLL|AUTHZ.DLL|AVICAP32.DLL|AVIFIL32.DLL|
|CABINET.DLL|CLUSAPI.DLL|COMCTL32.DLL|COMDLG32.DLL|
|COMSVCS.DLL|CREDUI.DLL|CRYPT32.DLL|CRYPTNET.DLL|
|CRYPTUI.DLL|D3D8THK.DLL|DBGENG.DLL|DBGHELP.DLL|
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP.DLL|DSUIEXT.DLL|
|GDI32.DLL|GLU32.DLL|HLINK.DLL|ICM32.DLL|
|IMAGEHLP.DLL|IMM32.DLL|IPHLPAPI.DLL|IPROP.DLL|
|KERNEL32.DLL|KSUSER.DLL|LOADPERF.DLL|LZ32.DLL|
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC.DLL|MPR.DLL|
|MPRAPI.DLL|MQRT.DLL|MSACM32.DLL|MSCMS.DLL|
|MSI.DLL|MSIMG32.DLL|MSRATING.DLL|MSTASK.DLL|
|MSVFW32.DLL|MSWSOCK.DLL|MTXEX.DLL|NDDEAPI.DLL|
|NETAPI32.DLL|NPPTOOLS。DLL|NTDSAPI.DLL|NTDSBCLI.DLL|
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32.DLL|
|OLEACC.DLL|OLEAUT32.DLL|OLEDLG.DLL|OPENGL32.DLL|
|PDH.DLL|POWRPROF.DLL|QOSNAME.DLL|查询。DLL|
|RASAPI32.DLL|RASDLG.DLL|RASSAPI.DLL|RESUTILS。DLL|
|RICHED20.DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|
|RTUTILS。DLL|SCARDDLG.DLL|SECUR32.DLL|SENSAPI.DLL|
|SETUPAPI.DLL|SFC.DLL|SHELL32.DLL|SHFOLDER。DLL|
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT。DLL|
|STI.DLL|TAPI32.DLL|TRAFFIC.DLL|URL.DLL|
|URLMON。DLL|USER32.DLL|USERENV.DLL|USP10.DLL|
|UXTHEME.DLL|VDMDBG.DLL|版本。DLL|WINFAX.DLL|
|WINHTTP.DLL|WININET.DLL|WINMM.DLL|WINSCARD.DLL|
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2_32.DLL|
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|

> [!NOTE]
>  由 CLR 代码，在同一模块中使用的非托管函数不支持保留的最后一个错误。

- 有关详细信息，请参阅 [/clr（公共语言运行时编译）](clr-common-language-runtime-compilation.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 点击“命令行”  属性页。

1. 该选项键入**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="example"></a>示例

下面的示例定义一个修改上一个错误的导出函数的本机 DLL。

```
// CLRSUPPORTLASTERROR_dll.cpp
// compile with: /LD
#include <windows.h>
#include <math.h>

#pragma unmanaged
__declspec(dllexport) double MySqrt(__int64 n) {
   SetLastError(DWORD(-1));
   return sqrt(double(n));
}
```

## <a name="example"></a>示例

下面的示例使用此 DLL，演示如何使用 **/CLRSUPPORTLASTERROR**。

```
// CLRSUPPORTLASTERROR_client.cpp
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll
// processor: x86
#include <windows.h>
#include <wininet.h>
#include <stdio.h>
#include <math.h>

#pragma comment(lib, "wininet.lib")

double MySqrt(__int64 n);

#pragma managed
int main() {
   double   d = 0.0;
   __int64 n = 65;
   HANDLE  hGroup = NULL;
   GROUPID groupID;
   DWORD   dwSet = 127, dwGet = 37;

   SetLastError(dwSet);
   d = MySqrt(n);
   dwGet = GetLastError();

   if (dwGet == DWORD(-1))
      printf_s("GetLastError for application call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for application call failed (%d).\n",
             dwGet);

   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,
                           0, 0, &groupID, 0);
   dwGet = GetLastError();
   if (dwGet == 183)
      printf_s("GetLastError for system call succeeded (%d).\n",
             dwGet);
   else
      printf_s("GetLastError for system call failed (%d).\n",
             dwGet);
}
```

```Output
GetLastError for application call failed (127).
GetLastError for system call succeeded (183).
```

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
