---
title: 已过时的函数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: conceptual
f1_keywords:
- is_wctype
- _loaddll
- _unloaddll
- _getdllprocaddr
- _seterrormode
- _beep
- _sleep
- _getsystime
- corecrt_wctype/is_wctype
- process/_loaddll
- process/_unloaddll
- process/_getdllprocaddr
- stdlib/_seterrormode
- stdlib/_beep
- stdlib/_sleep
- time/_getsystime
- time/_setsystime
dev_langs:
- C++
helpviewer_keywords:
- obsolete functions
- _beep function
- _sleep function
- _seterrormode function
ms.assetid: 8e14c2d4-1481-4240-8586-47eb43db02b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6fcb14a91aadb01d3962758b19ce636fddfbe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="obsolete-functions"></a>已过时的函数
某些库函数已过时，已有最新的等效函数。 我们建议改用更新版本。 已从 CRT 中删除其他过时函数。 本主题列出了已弃用的过时函数以及在 Visual Studio 特定版本中删除的函数。  
  
## <a name="deprecated-as-obsolete-in-visual-studio-2015"></a>在 Visual Studio 2015 中已弃用（过时）  
  
|已过时的函数|替代项|  
|-----------------------|-----------------|  
|`is_wctype`|[iswctype](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|  
|`_loaddll`|[LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)、 [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?LinkID=236091)或 [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159\(v=vs.85\).aspx)|  
|`_unloaddll`|[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)|  
|`_getdllprocaddr`|[GetProcAddress](../build/getprocaddress.md)|  
|`_seterrormode`|[SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242)|  
|`_beep`|[提示音](https://msdn.microsoft.com/library/windows/desktop/ms679277\(v=vs.85\).aspx)|  
|`_sleep`|[休眠](https://msdn.microsoft.com/library/windows/desktop/ms686298\(v=vs.85\).aspx)|  
|`_getsystime`|[GetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724338\(v=vs.85\).aspx)|  
|`_setsystime`|[SetLocalTime](https://msdn.microsoft.com/library/windows/desktop/ms724936\(v=vs.85\).aspx)|  
  
## <a name="removed-from-the-crt-in-visual-studio-2015"></a>已从 Visual Studio 2015 的 CRT 中删除  
  
|已过时的函数|替代项|  
|-----------------------|-----------------|  
|[_cgets、_cgetws](../c-runtime-library/cgets-cgetws.md)|[_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|  
|[gets、_getws](../c-runtime-library/gets-getws.md)|[gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|  
|[_get_output_format](../c-runtime-library/get-output-format.md)|无|  
|[_heapadd](../c-runtime-library/heapadd.md)|无|  
|[_heapset](../c-runtime-library/heapset.md)|无|  
|[inp、inpw](../c-runtime-library/inp-inpw.md)|无|  
|[_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)|无|  
|[outp、outpw](../c-runtime-library/outp-outpw.md)|无|  
|[_outp、_outpw、_outpd](../c-runtime-library/outp-outpw-outpd.md)|无|  
|[_set_output_format](../c-runtime-library/set-output-format.md)|无|  
  
## <a name="removed-from-the-crt-in-earlier-versions-of-visual-studio"></a>已从 Visual Studio 早期版本的 CRT 中删除  
 [_lock](../c-runtime-library/lock.md)  
  
 [_unlock](../c-runtime-library/unlock.md)