---
title: "-防护 （启用防护检查） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 48abdc4f923ed01ecba482b82da897d06fd56dcd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="guard-enable-guard-checks"></a>/GUARD（启用防护检查）
在可执行映像中，为控制流防护检查指定支持。  
  
## <a name="syntax"></a>语法  
  
```  
/GUARD:{CF|NO}  
```  
  
## <a name="remarks"></a>备注  
 当指定 /GUARD:CF 时，链接器将修改 .dll 或 .exe 的标头，以指示支持控制流防护 (CFG) 运行时检查。 链接器还会将所需的控制流目标地址数据添加到标头。 默认情况下，禁用 /GUARD:CF。 可以通过使用 /GUARD:NO 显式禁用。 为了提高效率，/guard: cf 还需要[/DYNAMICBASE （使用地址空间布局随机化）](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)链接器选项，默认是打开的。  
  
 通过使用编译源代码时[/guard: cf](../../build/reference/guard-enable-control-flow-guard.md)选项，编译器将分析通过检查对可能目标地址的所有间接调用来控制流。 编译器将插入代码，以验证间接调用指令的目标地址在运行时是否处于已知的目标地址列表中。 支持 CFG 的操作系统将停止未能通过 CFG 运行时检查的程序。 这提高了攻击者使用数据损坏来更改调用目标，以执行恶意代码的难度。  
  
 必须对编译器和链接器指定 /GUARD:CF 选项，以创建支持 CFG 的可执行映像。 编译但未使用 /GUARD:CF 链接的代码会产生运行时检查开销，但不会启用 CFG 保护。 当指定 /guard: cf 选项`cl`命令，编译并链接在一个步骤中，编译器将标志传递到链接器。 当**控制流防护**在 Visual Studio 中设置属性、 /guard: cf 选项传递给编译器和链接器。 当单独编译对象文件或库时，必须显式指定选项中`link`命令。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**配置属性**，**链接器**，**命令行**。  
  
3.  在**其他选项**，输入`/GUARD:CF`。  
  
## <a name="see-also"></a>请参阅  
 [/guard （启用控制流保护）](../../build/reference/guard-enable-control-flow-guard.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)