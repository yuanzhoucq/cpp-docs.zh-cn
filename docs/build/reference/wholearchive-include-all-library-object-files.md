---
title: "-WHOLEARCHIVE （包括所有库对象文件） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3499d6583c7d9801aa4c3b12c66196c975b192ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE （包括所有库对象文件）
Force 链接器包含在静态库链接的可执行文件中的所有对象文件。  
  
## <a name="syntax"></a>语法  
  
> / WHOLEARCHIVE [:*库*]  
  
## <a name="remarks"></a>备注  
  
/WHOLEARCHIVE 选项强制链接器指定的静态库，包括从每个对象文件或如果指定未的库，则指定到链接的所有静态库的命令。 若要指定多个库的 /WHOLEARCHIVE 选项，可以在链接器命令行上使用多个 /WHOLEARCHIVE 切换。 默认情况下，链接器包含对象中的文件的链接的输出仅当它们导出其他对象中的文件引用可执行文件的符号。 /WHOLEARCHIVE 选项，使链接器将如同它们链接器命令行上单独指定存档在静态库中的所有对象文件。  
  
/WHOLEARCHIVE 选项可用来重新导出静态库中的所有符号。 这可确保所有的库代码、 资源和元数据都包含时从多个静态库中创建的组件。 该库链接到另一个组件或应用程序时，如果你看到警告 LNK4264 创建静态库时包含导出的 Windows 运行时组件，使用 /WHOLEARCHIVE 选项。  
  
Visual Studio 2015 Update 2 中引入了 /WHOLEARCHIVE 选项。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
1.  选择**命令行**下的属性页**配置属性**，**链接器**。  
  
1.  添加到 /WHOLEARCHIVE 选项**其他选项**文本框。  
  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)