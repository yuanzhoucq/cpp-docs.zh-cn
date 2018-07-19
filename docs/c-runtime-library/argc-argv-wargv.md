---
title: __argc、__argv、__wargv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __wargv
- __argv
- __argc
apilocation:
- msvcrt120.dll
apitype: DLLExport
f1_keywords:
- __argv
- __argc
- __wargv
dev_langs:
- C++
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5d9762f02a06e697ce164910755431e8a59009
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390206"
---
# <a name="argc-argv-wargv"></a>__argc、__argv、__wargv
`__argc` 全局变量是传递给程序的命令行参数的数量计数。 `__argv` 是一个指向包含程序参数的单字节字符或多字节字符字符串的数组的指针，`__wargv` 是一个指向包含程序参数的宽字符字符串的数组的指针。 这些全局变量提供了 `main` 或 `wmain` 参数。  
  
## <a name="syntax"></a>语法  
  
```  
extern int __argc;  
extern char ** __argv;  
extern wchar_t ** __wargv;  
```  
  
## <a name="remarks"></a>备注  
 在使用 `main` 函数的程序中，将在程序启动时通过用于启动该程序的命令行来初始化 `__argc` 和 `__argv`。 会将命令行解析为单个自变量并展开通配符。 会将参数计数分配给 `__argc` 并在堆上分配参数字符串，以及将指向参数数组的指针分配给 `__argv`。 在编译为使用宽字符和 `wmain` 函数的程序中，将解析参数并将通配符展开为宽字符字符串，以及将指向参数字符串的数组的指针分配给 `__wargv`。  
  
 对于可移植代码，我们建议你使用传递给 `main` 的参数来获取程序中的命令行参数。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE|已定义 _UNICODE|  
|---------------------|---------------------------|-----------------------|  
|`__targv`|`__argv`|`__wargv`|  
  
## <a name="requirements"></a>惠?  
  
|全局变量|必需的标头|  
|---------------------|---------------------|  
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>、\<cstdlib> (C++)|  
  
 `__argc`、`__argv` 和 `__wargv` 是 Microsoft 扩展。 有关兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [全局变量](../c-runtime-library/global-variables.md)   
 [main：程序启动](../cpp/main-program-startup.md)   
 [使用 wmain 代替 main](../cpp/using-wmain-instead-of-main.md)