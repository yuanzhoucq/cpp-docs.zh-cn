---
title: "_execute_onexit_table、_initialize_onexit_table、_register_onexit_function |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs:
- C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d57452bb893ce86a9bddf949a9887eaf38e1cdbd

---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table、_initialize_onexit_table、_register_onexit_function
管理在退出时要调用的例程。  
  
## <a name="syntax"></a>语法  
  
```  
int _initialize_onexit_table(  
    _onexit_table_t* table  
    );  
  
int _register_onexit_function(  
    _onexit_table_t* table,  
    _onexit_t        function  
    );  
  
int _execute_onexit_table(  
    _onexit_table_t* table  
    );  
```  
  
#### <a name="parameters"></a>参数  
 [inout]`table`  
 指向 onexit 函数表的指针。  
  
 [in] `function`  
 指向一个函数以添加到 onexit 函数表的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回 0。 否则，返回一个负值。  
  
## <a name="remarks"></a>备注  
 这些函数是用来支持 C 运行时的基础结构实现详细信息，不应在代码中直接调用。 C 运行时使用 *onexit 函数表*来表示通过调用 `atexit`、`at_quick_exit`，和 `_onexit` 注册的函数序列。 onexit 函数表数据结构是 C 运行时的非跳转实现详细信息；可以更改此数据成员的顺序和含义。 它们不应由外部代码进行检查。  
  
 `_initialize_onexit_table` 函数将 onexit 函数表初始化为其初始值。  将 onexit 函数表传递给 `_register_onexit_function` 或 `_execute_onexit_table` 前，必须调用此函数。  
  
 `_register_onexit_function` 函数在 onexit 函数表的末尾追加一个函数。  
  
 `_execute_onexit_table` 函数执行 onexit 函数表中的所有函数，并清除表，然后返回。 在调用 `_execute_onexit_table` 后，表处于无效状态；必须通过调用 `_initialize_onexit_table` 以对其重新初始化后才能再次使用。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|  
  
 `_initialize_onexit_table`、`_register_onexit_function` 和 `_execute_onexit_table` 函数是 Microsoft 特定函数。 有关兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [atexit](../c-runtime-library/reference/atexit.md)   
 [exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)


<!--HONumber=Feb17_HO4-->


