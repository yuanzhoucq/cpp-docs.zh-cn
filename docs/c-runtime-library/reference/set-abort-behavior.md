---
title: "_set_abort_behavior | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_abort_behavior
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
dev_langs: C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: edf31ccddfb9ab2eaa6de226ff4ec7eb09869438
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="setabortbehavior"></a>_set_abort_behavior
指定当程序异常终止时要采取的操作。  
  
> [!NOTE]
>  不要使用 `abort` 函数关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用，除非在测试或调试方案中。 根据 [Windows 8 应用认证要求](http://go.microsoft.com/fwlink/?LinkId=262889)，禁止以编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用。 有关详细信息，请参阅[应用程序生命周期（Windows 应用商店应用）](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `flags`  
 `abort` 标志的新值。  
  
 [in] `mask`  
 要设置的 `abort` 标志位掩码。  
  
## <a name="return-value"></a>返回值  
 标志的旧值。  
  
## <a name="remarks"></a>备注  
 有两个 `abort` 标志：`_WRITE_ABORT_MSG` 和 `_CALL_REPORTFAULT`。 `_WRITE_ABORT_MSG` 确定在程序异常终止时是否打印有帮助的文本信息。 该消息声明应用程序已调用 `abort` 函数。 默认行为是打印该消息。 如果设置 `_CALL_REPORTFAULT`，则指定在调用 `abort` 时生成和报告 Watson 故障转储。 默认情况下，在非调试生成中启用故障转储报告。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_set_abort_behavior`|\<stdlib.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```C  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
```Output  
Suppressing the abort message. If successful, this message will be the only output.  
```  
  
## <a name="see-also"></a>另请参阅  
 [abort](../../c-runtime-library/reference/abort.md)