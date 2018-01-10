---
title: "_outp、_outpw、_outpd |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _outpw
- _outpd
- _outp
- outpd
dev_langs: C++
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: edcb3f8da6252705fe494acaa64c623b8a22ed3b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="outp-outpw-outpd"></a>_outp、_outpw、_outpd
按端口、字节 (`_outp`)、字 (`_outpw`) 或双字 (`_outpd`) 输出。  
  
> [!IMPORTANT]
>  这些函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供这些函数。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _outp(  
unsigned short port,  
int databyte   
);  
unsigned short _outpw(  
unsigned short port,  
unsigned short dataword   
);  
unsigned long _outpd(  
unsigned short port,  
unsigned long dataword   
);  
```  
  
#### <a name="parameters"></a>参数  
 *port*  
 端口号。  
  
 *databyte、dataword*  
 输出值。  
  
## <a name="return-value"></a>返回值  
 这些函数返回数据输出。 无错误返回。  
  
## <a name="remarks"></a>备注  
 `_outp`、 `_outpw`和 `_outpd` 函数分别将字节、字和双字写入指定的输出端口。 *port* 参数可为 0 - 65,535 范围内的任何无符号整数。*databyte* 可为 0 - 255 范围内的任何整数；*dataword* 可分别为整数、无符号短整数和无符号长整数范围内的任何值。  
  
 由于这些函数可直接写入到 I/O 端口，因此它们无法用于 Windows NT、Windows 2000、Windows XP 和 Windows Server 2003 中的用户代码。 有关在这些操作系统中使用 I/O 端口的信息，请在 MSDN 上搜索“Win32 中的串行通信”。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_outp`|\<conio.h>|  
|`_outpw`|\<conio.h>|  
|`_outpd`|\<conio.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [控制台和端口 I/O](../c-runtime-library/console-and-port-i-o.md)   
 [_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)