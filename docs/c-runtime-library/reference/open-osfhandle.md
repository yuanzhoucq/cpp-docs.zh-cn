---
title: "_open_osfhandle | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _open_osfhandle
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 0a201fa08f48198069df26c5c61944c99db73edf
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="openosfhandle"></a>_open_osfhandle
将 C 运行时文件描述符与现有操作系统文件句柄关联。  
  
## <a name="syntax"></a>语法  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### <a name="parameters"></a>参数  
 `osfhandle`  
 操作系统文件句柄。  
  
 `flags`  
 允许的操作类型。  
  
## <a name="return-value"></a>返回值  
 如果成功，`_open_osfhandle` 返回 C 运行时文件描述符。 否则，它将返回-1。  
  
## <a name="remarks"></a>备注  
 `_open_osfhandle` 函数分配 C 运行时文件描述符，并将其与由 `osfhandle` 指定的操作系统文件句柄相关联。 `flags` 参数是一个整数表达式，是由在 Fcntl.h 中定义的一个或多个清单常量组合构成。 当使用两个或多个清单常量来形成 `flags` 自变量时，这些常量将与按位 OR 运算符合并 (**&#124;**)。  
  
 Fcntl.h 定义以下清单常量。  
  
 **_O_APPEND**  
 在执行每个写入操作之前，将文件指针定位到文件结尾。  
  
 **_O_RDONLY**  
 打开文件以供只读。  
  
 **_O_TEXT**  
 在文本（转换）模式下打开文件。  
  
 **_O_WTEXT**  
 在 Unicode（转换 UTF-16）模式下打开文件。  
  
 若要关闭使用 `_open_osfhandle` 打开的文件，请调用 `_close`。 基础句柄也通过调用 `_close` 关闭，因此对原始句柄调用 Win32 函数 `CloseHandle` 是不必要的。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_open_osfhandle`|\<io.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)
