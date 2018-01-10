---
title: "-Zc: auto （推导变量类型） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc:auto
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd2f0ff353e1243685c94da0c28f29e810b2a9ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto（推导变量类型）
**/Zc: auto [-]**编译器选项指示编译器如何使用[auto 关键字](../../cpp/auto-keyword.md)来声明变量。 如果指定默认选项， **/zc: auto**，编译器会将从其初始化表达式声明的变量的类型推导。 如果指定**/Zc:auto-**，编译器会将分配到自动存储类变量。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:auto[-]  
```  
  
## <a name="remarks"></a>备注  
 C++ 标准为 `auto` 关键字定义了初始和修订的含义。 之前[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，关键字声明自动存储类中的变量; 也就是说，一个变量，具有本地生存期。 从开始[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，关键字中推导声明的初始化表达式中的某个变量的类型。 使用**/zc: auto [-]**编译器选项，以告知编译器要使用的原始或修订的含义`auto`关键字。  
  
 如果所使用的 `auto` 关键字与当前编译器选项发生冲突，编译器会发出适当的诊断消息。 有关详细信息，请参阅[auto 关键字](../../cpp/auto-keyword.md)。 有关使用 Visual c + + 一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**配置属性**节点。  
  
3.  单击**C/c + +**节点。  
  
4.  单击**命令行**节点。  
  
5.  添加**/zc: auto**或**/Zc:auto-**到**其他选项：**窗格。  
  
## <a name="see-also"></a>请参阅  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)   
 [auto 关键字](../../cpp/auto-keyword.md)