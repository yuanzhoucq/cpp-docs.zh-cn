---
title: /CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码）
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322279"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码）

**/CLRSUPPORTLASTERROR（** 默认情况下处于打开状态）保留了通过 P/Invoke 机制调用的函数的最后错误代码，该机制允许您从使用 **/clr**编译的代码调用 DLLS 中的本机函数。

## <a name="syntax"></a>语法

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>备注

保留最后一个错误代码意味着性能下降。  如果不想对保留最后一个错误代码的性能产生影响，请链接与 **/CLRSUPPORTLASTERROR：NO**。

您可以通过链接到 **/CLRSUPPORTLASTERROR：SYSTEMDLL**来最小化性能影响，后者仅保留系统 DlL 中函数的最后错误代码。  系统 DLL 定义为以下之一：

|||||
|-|-|-|-|
|ACLUI.Dll|活动。Dll|ADPTIF。Dll|ADVAPI32.Dll|
|ASYCFILT.Dll|奥特赫。Dll|AVICAP32.Dll|AVIFIL32.Dll|
|内阁。Dll|CLUSAPI。Dll|COMCTL32.Dll|COMDLG32.Dll|
|COMSVCS.Dll|瑞德威Dll|CRYPT32.Dll|密码网。Dll|
|CRYPTUI。Dll|D3D8THK.Dll|DBGENG。Dll|DBGHELP。Dll|
|DCIMAN32.Dll|DNSAPI。Dll|DSPROP.Dll|DSUIEXT.Dll|
|GDI32.Dll|GLU32.Dll|HLINK。Dll|ICM32.Dll|
|图像HLP。Dll|IMM32.Dll|IPHLPAPI。Dll|IPROP。Dll|
|内核32.Dll|KSUSER。Dll|LOADPERF.Dll|LZ32.Dll|
|MAPI32.Dll|MGMTAPI。Dll|MOBSYNC。Dll|Mpr。Dll|
|MPRAPI。Dll|MQRT。Dll|MSACM32.Dll|MSCMS。Dll|
|微星。Dll|MSIMG32.Dll|放大缩小字体功能 放大缩小字体功能Dll|MSTASK。Dll|
|MSVFW32.Dll|姆索科克Dll|MTXEX.Dll|NDDEAPI。Dll|
|NETAPI32.Dll|NPPTOOLS。Dll|NTDSAPI。Dll|NTDSBCLI。Dll|
|NTMSAPI。Dll|ODBC32.Dll|ODBCBCP.Dll|OLE32.Dll|
|OLEACC.Dll|奥莱奥特32。Dll|OLEDLG.Dll|OPENGL32.Dll|
|Pdh。Dll|POWRPROF.Dll|QOSNAME。Dll|查询。Dll|
|拉萨皮32。Dll|RASDLG.Dll|RASSAPI。Dll|RESUTILS。Dll|
|富德20。Dll|RPCNS4.Dll|RPCRT4.Dll|Rtm。Dll|
|RTUTILS.Dll|斯卡德格Dll|安全32。Dll|SENSAPI。Dll|
|设置API。Dll|证监会。Dll|SHELL32.Dll|舒斯里Dll|
|SHLWAPI。Dll|SISBKUP。Dll|SNMPAPI。Dll|SRCLIENT。Dll|
|性病。Dll|TAPI32.Dll|交通。Dll|Url。Dll|
|URLMON。Dll|用户32。Dll|USERENV.Dll|USP10.Dll|
|UXTHEME.Dll|VDMDBG。Dll|版本。Dll|温法克斯Dll|
|温HTTP。Dll|威尼内特Dll|温MM。Dll|温斯卡Dll|
|赢得信任。Dll|WLDAP32。Dll|哇32。Dll|WS2_32.DLL|
|WSNMP32.Dll|WSOCK32.DLL|WTSAPI32.Dll|XOLEHLP.Dll|

> [!NOTE]
> CLR 代码在同一模块中使用的非托管函数不支持保留最后一个错误。

- 有关更多信息，请参见 [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击“链接器”文件夹****。

1. 点击“命令行” **** 属性页。

1. 在"**附加选项**"框中键入该选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="example"></a>示例

以下示例使用一个导出的函数定义本机 DLL，该函数修改上次错误。

```cpp
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

以下示例使用 DLL，演示如何使用 **/CLRSUPPORTLASTERROR**。

```cpp
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

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
