---
title: "_purecall | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs:
- C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c19324cde907f31ab18a312f3039c2da7a3a40c7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="purecall"></a>_purecall
默认纯虚拟函数调用错误处理程序。 当调用纯虚拟成员函数时，编译器生成调用此函数的代码。  
  
## <a name="syntax"></a>语法  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## <a name="remarks"></a>备注  
 `_purecall` 函数是 Microsoft Visual C++ 编译器的 Microsoft 专用实现细节。 此函数不可以直接通过代码调用，也没有任何公用标头声明。 之所以在这里讨论此函数，是因为它是 C 运行时库的公用导出。  
  
 对纯虚拟函数的调用出错，因为它没有实现。 当调用纯虚拟函数时，编译器生成代码以调用 `_purecall` 错误处理程序函数。 默认情况下，`_purecall` 终止此程序。 在终止之前，`_purecall` 函数调用 `_purecall_handler` 函数（如果已为进程设置了该函数）。 可以安装自己的错误处理程序进行纯虚拟函数调用，以捕获这些调用用于调试和报告目的。 若要使用自己的错误处理程序，请创建一个具有 `_purecall_handler` 签名的函数，然后使用 [_set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) 使其成为当前处理程序。  
  
## <a name="requirements"></a>要求  
 `_purecall` 函数没有标头声明。 `_purecall_handler` typedef 在 \<stdlib.h 1> 中定义。  
  
## <a name="see-also"></a>请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_purecall_handler、_set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)