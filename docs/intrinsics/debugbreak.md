---
title: "__debugbreak |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs: C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07cac11754a8b5f242c38d5fd45d4c7f0707d69a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="debugbreak"></a>__debugbreak
**Microsoft 专用**  
  
 将在代码中引起断点，并在其中提示用户运行调试程序。  
  
## <a name="syntax"></a>语法  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|Header|  
|---------------|------------------|------------|  
|`__debugbreak`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
  
## <a name="remarks"></a>备注  
 `__debugbreak`编译器内部函数，类似于[DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)，是用于引起断点的可移植 Win32 方式。  
  
> [!NOTE]
>  使用编译时**/clr**，函数包含`__debugbreak`将编译为 MSIL。 `asm int 3` 可将函数编译为本机函数。 有关详细信息，请参阅[__asm](../assembler/inline/asm.md)。  
  
 例如:  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 类似于：  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 在 x86 计算机上。  
  
 此例程仅可用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [关键字](../cpp/keywords-cpp.md)