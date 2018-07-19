---
title: -ZW （Windows 运行时编译） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fce6c6825ed4ae715a2f4cde6b0e1ffa8b3b6733
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380061"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW（Windows 运行时编译）
编译源代码以支持[!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) 创建的通用 Windows 平台 (UWP) 应用。  
  
 当你使用 **/ZW**进行编译时，始终指定 **/EHsc**以及。  
  
## <a name="syntax"></a>语法  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>自变量  
 nostdlib  
 指示 Platform.winmd、Windows.Foundation.winmd 以及其他默认 Windows 元数据 (.winmd) 文件未自动包含在该编译中。 相反，你必须使用[/FU (命名强制 #using 文件)](../../build/reference/fu-name-forced-hash-using-file.md)编译器选项显式指定 Windows 元数据文件。  
  
## <a name="remarks"></a>备注  
 当指定 **/ZW**选项时，编译器将支持以下功能：  
  
-   必需的元数据文件、 命名空间、 数据类型和你的应用需要在 Windows 运行时中执行的函数中。  
  
-   自动引用计数的 Windows 运行时对象，并自动在其引用计数变为零时放弃的对象。  
  
 因为 incremental 链接器不支持通过使用.obj 文件中包含的 Windows 元数据 **/ZW**选项， [/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)选项与不兼容 **/ZW**.  
  
 有关详细信息，请参阅[Visual c + + 语言参考](../../cppcx/visual-c-language-reference-c-cx.md)。  
  
## <a name="requirements"></a>要求  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)