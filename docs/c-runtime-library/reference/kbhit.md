---
title: "_kbhit | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _kbhit
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
- _kbhit
- kbhit
- conio/_kbhit
dev_langs:
- C++
helpviewer_keywords:
- keyboard input
- user input, checking for keyboard
- kbhit function
- console
- console, checking
- keyboards, keyboard input
- _kbhit function
- keyboards, checking input
ms.assetid: e82a1cc9-bbec-4150-b678-a7e433220fe4
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: e213247266cad2c0f96b96057cf8e6933dfe45c6
ms.lasthandoff: 02/24/2017

---
# <a name="kbhit"></a>_kbhit
检查键盘输入的控制台。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
  
int _kbhit( void );  
```  
  
## <a name="return-value"></a>返回值  
 如果已按一个键，则 `_kbhit` 返回一个非零值。 否则返回 0。  
  
## <a name="remarks"></a>备注  
 `_kbhit` 函数检查最近键击的控制台。 如果函数返回一个非零值，则键击将在缓冲区中等待。 然后，程序可调用 `_getch` 或 `_getche` 来获取键击。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_kbhit`|\<conio.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
```  
// crt_kbhit.c  
// compile with: /c  
/* This program loops until the user  
 * presses a key. If _kbhit returns nonzero, a  
 * keystroke is waiting in the buffer. The program  
 * can call _getch or _getche to get the keystroke.  
 */  
  
#include <conio.h>  
#include <stdio.h>  
  
int main( void )  
{  
   /* Display message until key is pressed. */  
   while( !_kbhit() )  
      _cputs( "Hit me!! " );  
  
   /* Use _getch to throw key away. */  
   printf( "\nKey struck was '%c'\n", _getch() );  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!!  
Key struck was 'q'   
```  
  
## <a name="see-also"></a>另请参阅  
 [控制台和端口 I/O](../../c-runtime-library/console-and-port-i-o.md)
