---
title: "_set_SSE2_enable | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_SSE2_enable"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_SSE2_enable"
  - "set_SSE2_enable"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_SSE2_enable 函数"
  - "流式处理 SIMD 扩展 2 说明"
  - "set_SSE2_enable 函数"
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_SSE2_enable
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用或禁用CRT 算术例程中的 [流式处理 SIMD 扩展 2](http://msdn.microsoft.com/zh-cn/f98440eb-73a9-4f96-b203-ac41bb6701ea)\(SSE2\)的指令的使用。\(此函数上在x64架构上不可用，因为默认情况下启用SSE2。\)  
  
## 语法  
  
```  
int _set_SSE2_enable(  
   int flag  
);  
```  
  
#### 参数  
 `flag`  
 1是启用SSE2实现;0是禁用SSE2类型实现。  默认情况下，在支持它的处理器启用SSE2的实现。  
  
## 返回值  
 如果启用SSE2实现，则为非零；如果禁用SSE2实现，则为零。  
  
## 备注  
 下列函数具有通过`_set_SSE2_enable`启用的SSE2实现：  
  
-   [atan](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)  
  
-   [ceil](../../c-runtime-library/reference/ceil-ceilf-ceill.md)  
  
-   [exp](../../c-runtime-library/reference/exp-expf.md)  
  
-   [floor](../../c-runtime-library/reference/floor-floorf-floorl.md)  
  
-   [log](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [log10](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [modf](../../c-runtime-library/reference/modf-modff-modfl.md)  
  
-   [pow](../../c-runtime-library/reference/pow-powf-powl.md)  
  
 这些函数的SSE2实现可能产生某些与默认实现不同的答案，因为SSE2的中间值为 64 位浮点数，但默认实现中间值为 80 位浮点数。  
  
> [!NOTE]
>  如果使用 [\/Oi \(生成内部函数\)](../../build/reference/oi-generate-intrinsic-functions.md) 编译器选项编译项目，可能看起来像是 `_set_SSE2_enable`没有效果。  `/Oi` 编译器选项让编译器有权限使用内联函数替换CRT 调用；此行为重写 `_set_SSE2_enable`的效果。  如果要保证 `/Oi` 不可重写 `_set_SSE2_enable`，使用 `/Oi-` 编译项目。  当使用隐式 `/Oi`的其他编译器开关时，这也可能是一种好方法。  
  
 如果所有异常被屏蔽，才使用SSE2的实现。  使用 [\_control87，\_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 屏蔽异常。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_SSE2_enable`|\<math.h\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_set_SSE2_enable.c  
// processor: x86  
#include <math.h>  
#include <stdio.h>  
  
int main()  
{  
   int i = _set_SSE2_enable(1);  
  
   if (i)  
      printf("SSE2 enabled.\n");  
   else  
      printf("SSE2 not enabled; processor does not support SSE2.\n");  
}  
```  
  
 **Output**  
  
 `SSE2 enabled.`  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [CRT 库功能](../../c-runtime-library/crt-library-features.md)