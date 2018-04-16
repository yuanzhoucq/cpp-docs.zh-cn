---
title: -CLRTHREADATTRIBUTE （设置 CLR 线程特性） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1aae2dadc2fa7a8c9dc67780bb88b4da60d256e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE（设置 CLR 线程特性）
显式指定为 CLR 程序入口点的线程特性。  
  
## <a name="syntax"></a>语法  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### <a name="parameters"></a>参数  
 MTA  
 将该 MTAThreadAttribute 属性应用到你的程序的入口点。  
  
 无  
 与不指定 /CLRTHREADATTRIBUTE 相同。  允许公共语言运行时 (CLR) 设置默认线程特性。  
  
 STA  
 将该 STAThreadAttribute 属性应用到你的程序的入口点。  
  
## <a name="remarks"></a>备注  
 设置将 thread 特性有效时才生成.exe，因为它影响主线程的入口点。  
  
 如果你使用的默认入口点 （主数据连接或 wmain，例如） 指定的线程模型通过使用 /CLRTHREADATTRIBUTE 或放置线程处理特性 （STAThreadAttribute 或 MTAThreadAttribute） 上的默认条目函数。  
  
 如果你使用非默认入口点，指定通过使用 /CLRTHREADATTRIBUTE 或通过放置线程处理非默认入口函数中，属性，然后指定了具有非默认入口点的线程模型[/ENTRY](../../build/reference/entry-entry-point-symbol.md).  
  
 如果 /CLRTHREADATTRIBUTE 使用指定的线程模型不一致的源代码中指定的线程模型，将忽略 /CLRTHREADATTRIBUTE 链接器并将其应用源代码中指定的线程处理模型。  
  
 如果 CLR 程序承载使用单线程的 COM 对象，它将你使用单线程处理，例如，所必需的。  如果你 CLR 程序使用多线程处理，它不能承载使用单线程的 COM 对象。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**高级**属性页。  
  
5.  修改**CLR 线程特性**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)