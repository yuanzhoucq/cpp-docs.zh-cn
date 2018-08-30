---
title: __debugbreak |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9884cd8aec09bfcefaa8455457a3a4d3bb5b3d3d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219226"
---
# <a name="debugbreak"></a>__debugbreak
**Microsoft 专用**  
  
 将在代码中引起断点，并在其中提示用户运行调试程序。  
  
## <a name="syntax"></a>语法  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|Header|  
|---------------|------------------|------------|  
|`__debugbreak`|x86、 ARM、 x64|\<intrin.h>|  
  
## <a name="remarks"></a>备注  
 `__debugbreak`编译器内部函数，类似于[DebugBreak](https://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)，是会导致断点的可移植 Win32 方式。  
  
> [!NOTE]
>  使用编译时 **/clr**，一个函数，其中包含`__debugbreak`将编译为 MSIL。 `asm int 3` 可将函数编译为本机函数。 有关详细信息，请参阅[__asm](../assembler/inline/asm.md)。  
  
 例如：  
  
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