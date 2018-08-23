---
title: 加载被延迟加载的 DLL 的所有导入 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f054479a6681ba6de57690295fe3ce9f6c83696
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374367"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>加载被延迟加载的 DLL 的所有导入
**__HrLoadAllImportsForDll**函数，其定义中 delayhlp.cpp，通知链接器从指定的 DLL 加载所有导入[/delayload](../../build/reference/delayload-delay-load-import.md)链接器选项。  
  
 加载所有导入，可将放在代码中的一个位置中的错误处理，而不必使用异常处理的导入的实际调用周围。 它还可以避免在你的应用程序宿主即失败部分通过由于未能加载导入的帮助器代码的过程的情况。  
  
 调用 **__HrLoadAllImportsForDll**不会更改的行为挂钩和错误处理; 请参阅[错误处理和通知](../../build/reference/error-handling-and-notification.md)有关详细信息。  
  
 DLL 名称传递给 **__HrLoadAllImportsForDll**相比存储内 DLL 本身的名称和区分大小写。  
  
 下面的示例演示如何调用 **__HrLoadAllImportsForDll**:  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)