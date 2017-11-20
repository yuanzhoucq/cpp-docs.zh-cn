---
title: "_nolock 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- _nolock functions
- nolock functions
ms.assetid: 7d651d87-38d2-4303-9897-fdb5f7a3e899
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 769fce588307a559a5926dfb5374ccad72ed857b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="nolock-functions"></a>_nolock 函数
这些是不执行任何锁定的函数。 它们是为需要最佳性能的用户提供的。 有关详细信息，请参阅[多线程库性能](../c-runtime-library/multithreaded-libraries-performance.md)。  
  
 仅在您的程序是真正的单线程程序或自行锁定时，使用才可以使用 _nolock 函数。  
  
 [_fclose_nolock](../c-runtime-library/reference/fclose-nolock.md)  
  
 [_fflush_nolock](../c-runtime-library/reference/fflush-nolock.md)  
  
 [_fgetc_nolock、_fgetwc_nolock](../c-runtime-library/reference/fgetc-nolock-fgetwc-nolock.md)  
  
 [_fread_nolock](../c-runtime-library/reference/fread-nolock.md)  
  
 [_fseek_nolock、_fseeki64_nolock](../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)  
  
 [_ftell_nolock、_ftelli64_nolock](../c-runtime-library/reference/ftell-nolock-ftelli64-nolock.md)  
  
 [_fwrite_nolock](../c-runtime-library/reference/fwrite-nolock.md)  
  
 [_getc_nolock、_getwc_nolock](../c-runtime-library/reference/getc-nolock-getwc-nolock.md)  
  
 [_getch_nolock、_getwch_nolock](../c-runtime-library/reference/getch-nolock-getwch-nolock.md)  
  
 [_getchar_nolock、_getwchar_nolock](../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)  
  
 [_getche_nolock、_getwche_nolock](../c-runtime-library/reference/getche-nolock-getwche-nolock.md)  
  
 [_getdcwd_nolock、_wgetdcwd_nolock](../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)  
  
 [_putc_nolock、_putwc_nolock](../c-runtime-library/reference/putc-nolock-putwc-nolock.md)  
  
 [_putch_nolock、_putwch_nolock](../c-runtime-library/reference/putch-nolock-putwch-nolock.md)  
  
 [_putchar_nolock、_putwchar_nolock](../c-runtime-library/reference/putchar-nolock-putwchar-nolock.md)  
  
 [_ungetc_nolock、_ungetwc_nolock](../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)  
  
 [_ungetch_nolock、_ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)  
  
## <a name="see-also"></a>另请参阅  
 [输入和输出](../c-runtime-library/input-and-output.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)