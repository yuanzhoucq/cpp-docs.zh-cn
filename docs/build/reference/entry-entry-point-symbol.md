---
title: "输入 （入口点符号） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
dev_langs: C++
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ebaf9a8723f06b6fab8577abf283f6eec69aa25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="entry-entry-point-symbol"></a>/ENTRY（入口点符号）
```  
/ENTRY:function  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *函数*  
 一个函数，指定的用户定义起始地址的.exe 文件或 DLL。  
  
## <a name="remarks"></a>备注  
 /ENTRY 选项指定为一个.exe 文件或 DLL 的起始地址的入口点函数。  
  
 该函数必须定义要使用`__stdcall`调用约定。 参数和返回值取决于程序是否一个控制台应用程序、 windows 应用程序或 DLL。 建议你让链接器设置的入口点，以便 C 运行时库正确初始化，并执行的静态对象的 c + + 构造函数。  
  
 默认情况下，起始地址是从 C 运行时库函数名称。 链接器选择它的程序属性根据下表中所示。  
  
|功能名称|默认值为|  
|-------------------|-----------------|  
|**mainCRTStartup** (或**wmainCRTStartup**)|使用 /SUBSYSTEM:CONSOLE; 的应用程序调用`main`(或`wmain`)|  
|**WinMainCRTStartup** (或**wWinMainCRTStartup**)|使用 /SUBSYSTEM 的应用程序：**WINDOWS**; 调用`WinMain`(或`wWinMain`)，其必须定义为使用`__stdcall`|  
|**_DllMainCRTStartup**|DLL;调用`DllMain`如果它存在，其必须定义以使用`__stdcall`|  
  
 如果[/DLL](../../build/reference/dll-build-a-dll.md)或[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)未指定选项、 链接器选择的子系统和条目的点，具体取决于是否`main`或`WinMain`定义。  
  
 函数`main`， `WinMain`，和`DllMain`是三种形式的用户定义入口点。  
  
 创建托管的映像时，指定到 /ENTRY 的函数必须具有的签名 (LPVOID *var1*，DWORD *var2*，LPVOID *var3*)。  
  
 有关如何定义你自己的信息`DllMain`入口点，请参阅[Dll 和 Visual c + + 运行库行为](../../build/run-time-library-behavior.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**高级**属性页。  
  
4.  修改**入口点**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)