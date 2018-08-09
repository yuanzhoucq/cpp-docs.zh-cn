---
title: 包含共享 （只读） 或计算符号 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.shared.calculated
dev_langs:
- C++
helpviewer_keywords:
- symbols, read-only
- symbols, shared
- symbols, calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9eeaacf95040f0f7e2ee435a7fbed2c173076315
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014908"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>包含共享（只读）或计算符号
开发环境首次读取由其他应用程序创建的资源文件时，会将所有包含的头文件都标记为只读。 随后，可以使用[资源包括对话框的](../windows/resource-includes-dialog-box.md)添加其他只读符号头文件。  
  
 可能要使用只读符号定义的原因之一是用于计划在多个项目之间共享的符号文件。  
  
 当现有资源包含的符号定义使用表达式而不是简单整数来定义符号值时，也可以使用包含的符号文件。 例如：  
  
```cpp  
#define   IDC_CONTROL1 2100  
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```  
  
 只要满足以下条件，环境便会正确解释这些计算的符号：  
  
-   计算的符号置于只读符号文件中。  
  
-   资源文件包含已分配有这些计算的符号的资源。  
  
-   需要数值表达式。  
  
> [!NOTE]
>  如果需要字符串或数值表达式，则不会计算表达式。  
  
### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>在资源文件包含共享（只读）符号  
  
1.  在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择[资源包括](../windows/resource-includes-dialog-box.md)从快捷菜单。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在中**只读符号指令**框中，使用`#include`编译器指令，以指定想要保留只读符号的文件。  
  
     请勿调用文件`Resource.h`，因为它是通常由主符号头文件的文件名。  
  
    > [!NOTE]
    >  **重要**完全按照您键入您在只读符号指令框中键入包含资源文件中。 请确保输入的内容不包含任何拼写或语法错误。  
  
     使用**只读符号指令**框可包括仅限符号定义的文件。 请勿包含资源定义；否则，在保存文件时会创建重复的资源定义。  
  
3.  将符号置于指定的文件中。  
  
     采用这种方式包含的文件中的符号会在每次打开资源文件时进行计算，但是在保存文件时不会在磁盘上替换它们。  
  
4.  单击 **“确定”**。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [符号名限制](../windows/symbol-name-restrictions.md)   
 [符号值限制](../windows/symbol-value-restrictions.md)   
 [预定义的符号 Id](../windows/predefined-symbol-ids.md)   
 [符号：资源标识符](../windows/symbols-resource-identifiers.md)