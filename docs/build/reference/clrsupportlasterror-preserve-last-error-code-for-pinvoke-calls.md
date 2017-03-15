---
title: "/CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRSUPPORTLASTERROR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRSUPPORTLASTERROR 链接器选项"
  - "-CLRSUPPORTLASTERROR 链接器选项"
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /CLRSUPPORTLASTERROR（为 PInvoke 调用保留上次的错误代码）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/CLRSUPPORTLASTERROR** 默认情况下为开启状态，可保留通过 P\/Invoke 机制调用的函数的上一个错误代码，这样就可以从用 **\/clr** 编译的代码中调用 DLL 中的本机函数。  
  
## 语法  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## 备注  
 保留上一个错误代码意味着性能有所降低。如果不希望保留上一个错误代码对性能造成影响，可使用 **\/CLRSUPPORTLASTERROR:NO** 进行链接。  
  
 使用 **\/CLRSUPPORTLASTERROR:SYSTEMDLL** 进行链接时，仅为系统 DLL 中的函数保留上一个错误代码，可使性能影响达到最小。系统 DLL 定义为如下之一：  
  
|||||  
|-|-|-|-|  
|ACLUI.DLL|ACTIVEDS.DLL|ADPTIF.DLL|ADVAPI32.DLL|  
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
|NETAPI32.DLL|NPPTOOLS.DLL|NTDSAPI.DLL|NTDSBCLI.DLL|  
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32.DLL|  
|OLEACC.DLL|OLEAUT32.DLL|OLEDLG.DLL|OPENGL32.DLL|  
|PDH.DLL|POWRPROF.DLL|QOSNAME.DLL|QUERY.DLL|  
|RASAPI32.DLL|RASDLG.DLL|RASSAPI.DLL|RESUTILS.DLL|  
|RICHED20.DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|  
|RTUTILS.DLL|SCARDDLG.DLL|SECUR32.DLL|SENSAPI.DLL|  
|SETUPAPI.DLL|SFC.DLL|SHELL32.DLL|SHFOLDER.DLL|  
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT.DLL|  
|STI.DLL|TAPI32.DLL|TRAFFIC.DLL|URL.DLL|  
|URLMON.DLL|USER32.DLL|USERENV.DLL|USP10.DLL|  
|UXTHEME.DLL|VDMDBG.DLL|VERSION.DLL|WINFAX.DLL|  
|WINHTTP.DLL|WININET.DLL|WINMM.DLL|WINSCARD.DLL|  
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2\_32.DLL|  
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|  
  
> [!NOTE]
>  在相同模块中，CLR 代码使用的非托管函数不支持保留上一个错误。  
  
-   有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 示例  
 下面的示例定义一个本机 DLL，该 DLL 具有一个修改上一个错误的导出函数。  
  
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
  
## 示例  
 下面的示例使用该 DLL，演示如何使用 **\/CLRSUPPORTLASTERROR**。  
  
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
  
  **GetLastError用于应用程序调用失败 \(127\)。**  
**GetLastError用于系统调用成功 \(183\)。**   
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)