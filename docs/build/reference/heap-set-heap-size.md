---
title: "-HEAP （设置堆大小） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
dev_langs:
- C++
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd4ba44a76fa7881ebee2ec2f472dad8675e2c8
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="heap-set-heap-size"></a>/HEAP（设置堆大小）
```  
/HEAP:reserve[,commit]  
```  
  
## <a name="remarks"></a>备注  
 /HEAP 选项以字节为单位设置堆的大小。 生成的.exe 文件时，此选项是仅供使用。  
  
 *保留*自变量指定虚拟内存中堆分配总量。 默认堆大小为 1 MB。 链接器将指定的值与最接近的 4 个字节向上舍入。  
  
 可选`commit`参数指定要一次分配的物理内存量。 提交的虚拟内存后，要分页文件中保留的空间。 更高`commit`值可以节省的时间，当应用程序需要更多堆空间，但会增加内存需求并可能延长启动时间。  
  
 指定*保留*和`commit`以十进制或 C 语言表示法的值。  
  
 此功能还可通过以下方式使用的模块定义文件[HEAPSIZE](../../build/reference/heapsize.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**系统**属性页。  
  
4.  修改**堆提交大小**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)