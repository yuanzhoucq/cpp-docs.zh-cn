---
title: -GT （支持纤程安全线程本地存储区） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs:
- C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 493199cf4d5e66a866fbaa87aafc4098c3114cf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373824"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT（支持纤程安全的线程本地存储区）
支持使用静态线程本地存储，即与分配的数据分配的数据的纤程安全`__declspec(thread)`。  
  
## <a name="syntax"></a>语法  
  
```  
/GT  
```  
  
## <a name="remarks"></a>备注  
 使用声明数据`__declspec(thread)`通过线程本地存储 (TLS) 数组引用。 TLS 数组是为系统维护每个线程的地址的数组。 此数组中的每个地址提供的线程本地存储数据的位置。  
  
 纤程由堆栈和寄存器上下文组成，可以安排在各种线程的轻量级对象。 纤程可以在任何线程上运行。 因为纤程可能会交换出，稍后在重新启动另一个线程，TLS 数组的地址必须不需要缓存或优化作为公共子表达式在函数调用 (请参阅[/Og （全局优化）](../../build/reference/og-global-optimizations.md)选项详细信息）。 **/GT**可防止这种优化。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**优化**属性页。  
  
4.  修改**启用纤程安全优化**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)