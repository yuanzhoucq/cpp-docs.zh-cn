---
title: -CLRSUPPORTLASTERROR （保留最后一个错误代码为 PInvoke 调用） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRSUPPORTLASTERROR
dev_langs:
- C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 297414aa71e9d871da795c2ffe567573237c7e0e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378631"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码）
**/CLRSUPPORTLASTERROR**，这是在默认情况下，使用保留通过 P/Invoke 机制，可用于在 DLL，从代码调用本机函数调用的函数的最后一个错误代码编译 **/clr**。  
  
## <a name="syntax"></a>语法  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## <a name="remarks"></a>备注  
 保留的最后一个错误代码意味着导致性能降低。  如果您不想要对性能造成影响的保留的最后一个错误代码，与链接 **/CLRSUPPORTLASTERROR:NO**。  
  
 你可以通过链接性能影响降至最低 **/CLRSUPPORTLASTERROR:SYSTEMDLL**，从而仅保留在系统 Dll 中的函数的最后一个错误代码。  系统 DLL 定义为以下项之一：  
  
|||||  
|-|-|-|-|  
|ACLUI。DLL|ACTIVEDS。DLL|ADPTIF。DLL|ADVAPI32。DLL|  
|ASYCFILT。DLL|授权。DLL|AVICAP32。DLL|AVIFIL32。DLL|  
|CAB 文件。DLL|CLUSAPI。DLL|COMCTL32。DLL|COMDLG32。DLL|  
|COMSVCS。DLL|CREDUI。DLL|CRYPT32。DLL|CRYPTNET。DLL|  
|CRYPTUI。DLL|D3D8THK。DLL|DBGENG。DLL|DBGHELP。DLL|  
|DCIMAN32。DLL|DNSAPI。DLL|DSPROP。DLL|DSUIEXT。DLL|  
|GDI32。DLL|GLU32。DLL|HLINK。DLL|ICM32。DLL|  
|了内部错误。DLL|IMM32。DLL|IPHLPAPI。DLL|IPROP。DLL|  
|KERNEL32。DLL|KSUSER。DLL|LOADPERF。DLL|LZ32。DLL|  
|MAPI32。DLL|MGMTAPI。DLL|MOBSYNC。DLL|MPR。DLL|  
|MPRAPI。DLL|MQRT。DLL|MSACM32。DLL|MSCMS。DLL|  
|MSI。DLL|MSIMG32。DLL|MSRATING。DLL|MSTASK。DLL|  
|MSVFW32。DLL|MSWSOCK。DLL|MTXEX。DLL|NDDEAPI。DLL|  
|NETAPI32。DLL|NPPTOOLS。DLL|NTDSAPI。DLL|NTDSBCLI。DLL|  
|NTMSAPI。DLL|ODBC32。DLL|ODBCBCP。DLL|OLE32。DLL|  
|OLEACC。DLL|OLEAUT32。DLL|OLEDLG。DLL|OPENGL32。DLL|  
|PDH。DLL|POWRPROF。DLL|QOSNAME。DLL|查询。DLL|  
|RASAPI32。DLL|RASDLG。DLL|RASSAPI。DLL|RESUTILS。DLL|  
|RICHED20。DLL|RPCNS4。DLL|RPCRT4。DLL|RTM。DLL|  
|RTUTILS。DLL|SCARDDLG。DLL|SECUR32。DLL|SENSAPI。DLL|  
|安装程序 API。DLL|SFC。DLL|SHELL32。DLL|SHFOLDER。DLL|  
|SHLWAPI。DLL|SISBKUP。DLL|SNMPAPI。DLL|SRCLIENT。DLL|  
|STI。DLL|TAPI32。DLL|流量。DLL|URL。DLL|  
|URLMON。DLL|USER32。DLL|USERENV。DLL|USP10。DLL|  
|UXTHEME。DLL|VDMDBG。DLL|版本。DLL|WINFAX。DLL|  
|WINHTTP。DLL|WININET。DLL|WINMM。DLL|WINSCARD。DLL|  
|WINTRUST。DLL|WLDAP32 会。DLL|WOW32。DLL|WS2_32.DLL|  
|WSNMP32。DLL|WSOCK32.DLL|WTSAPI32。DLL|XOLEHLP。DLL|  
  
> [!NOTE]
>  由 CLR 代码，同一模块中使用的非托管函数不支持保留的最后一个错误。  
  
-   有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  该选项键入**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="example"></a>示例  
 下面的示例定义与一个导出的函数修改最后一个错误是本机 DLL。  
  
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
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)