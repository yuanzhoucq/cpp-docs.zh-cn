---
title: "链接器工具错误 LNK1123 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1123"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1123"
ms.assetid: fe47af69-0f42-4792-9133-541192cd8514
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 链接器工具错误 LNK1123
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

转换到 COFF 期间失败：文件无效或损坏  
  
 输入文件必须具有通用对象文件格式 \(COFF\) 格式。  如果输入文件不是 COFF，LINK 则链接器会自动尝试将 32 位 OMF 对象转换为 COFF，或运行 CVTRES.EXE 来转换资源文件。  此消息指示链接器不能转换该文件。  从另一个安装的 Visual Studio、Windows 开发工具包或 .NET Framework 中使用不兼容的 CVTRES.EXE 版本时，也会出现此情况。  
  
> [!NOTE]
>  如果你运行的是早期版本的 Visual Studio，则自动转换可能不受支持。  
  
### 修复此问题  
  
-   将所有服务包和更新应用到你的 Visual Studio 版本。  这对于 Visual Studio 2010 尤为重要。  
  
-   禁用了尝试使用增量链接生成。  在菜单栏上，依次选择“项目”、“属性”。  在“属性页”对话框中，依次展开“配置属性”、“链接器”。  将“启用增量链接”的值更改为“否”。  
  
-   验证在 PATH 环境变量中首次发现的 CVTRES.EXE 版本是否与由你的项目使用的生成工具的版本或平台工具集的版本相匹配。  
  
-   尝试关闭嵌入清单选项。  在菜单栏上，依次选择“项目”、“属性”。  在**“属性页”**对话框中，展开**“配置属性”**、**“清单工具”**、**“输入和输出”**。  将**“嵌入清单”**的值更改为**“否”**。  
  
-   确保文件类型有效。  例如，确保 OMF 对象是 32 位而不是 16 位。  有关详细信息，请参阅[用作链接器输入的 .Obj 文件](../../build/reference/dot-obj-files-as-linker-input.md)和 [Microsoft PE 和 COFF 规范](http://go.microsoft.com/fwlink/p/?LinkId=93292)。  
  
-   确保文件未损坏。  如有必要，请重新生成。  
  
## 请参阅  
 [用作链接器输入的 .Obj 文件](../../build/reference/dot-obj-files-as-linker-input.md)   
 [EDITBIN 参考](../../build/reference/editbin-reference.md)   
 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)