---
title: -TLBID （指定类型库的资源 ID） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
dev_langs:
- C++
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acea8de3f656da54a0697dc5b980dd4913054a00
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375160"
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID（指定类型库的资源 ID）
```  
/TLBID:id  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 `id`  
 一个用户指定的值，链接器创建类型库。 它重写默认资源 ID 为 1。  
  
## <a name="remarks"></a>备注  
 在编译时使用特性的程序，链接器将创建类型库。 链接器将分配到类型库的资源 ID 为 1。  
  
 如果此资源 ID 与某个现有资源的冲突，你可以使用 /TLBID 指定其他 ID。 可以将传递到的值的范围`id`是 1 到 65535。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**嵌入 IDL**属性页。  
  
4.  修改**类型库资源 ID**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)