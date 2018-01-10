---
title: "-HIGHENTROPYVA (支持 64 位 ASLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 059f6169cafc48fc67587ae2f5827966269e6ac7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA（支持 64 位 ASLR）
指定可执行映像支持高熵（64 位）地址空间布局随机化 (ASLR)。  
  
## <a name="syntax"></a>语法  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，为 64 位可执行映像打开 /HIGHENTROPYVA。 它不适用于 32 位可执行图像。 若要启用此选项，/DYNAMICBASE 也必须处于打开状态。  
  
 /HIGHENTROPYVA 修改 .dll 文件或 .exe 文件的标头，以指示是否支持 64 位地址的 ASLR。 当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来重新设定可执行图像段。 更大的地址空间使攻击者更难猜到特定内存区域的位置。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**节点。  
  
3.  展开**链接器**节点。  
  
4.  选择**命令行**属性页。  
  
5.  在**其他选项**，输入`/HIGHENTROPYVA`或`/HIGHENTROPYVA:NO`。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)