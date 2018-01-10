---
title: "-vd （禁用构造置换） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /vd
dev_langs: C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b945c4a3191554d5299522ff376772d6362a616c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vd-disable-construction-displacements"></a>/vd（禁用构造置换）
## <a name="syntax"></a>语法  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>自变量  
 `0`  
 取消 vtordisp 构造函数/析构函数置换成员。 选择此选项仅当你确信所有类的构造函数和析构函数都调用虚函数几乎。  
  
 `1`  
 允许隐藏的 vtordisp 构造函数/析构函数置换成员的创建。 此选项是默认值。  
  
 `2`  
 允许你使用[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)上正在构造的对象。 例如，dynamic_cast 从虚拟基类派生的类。  
  
 **/vd2**当具有虚拟基具有虚函数时添加一个 vtordisp 字段。 **/vd1**就足够了。 最常见情况**/vd2**是必需的虚拟基中的唯一虚函数是析构函数时。  
  
## <a name="remarks"></a>备注  
 这些选项仅适用于使用虚拟基的 c + + 代码。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]在使用虚拟继承的情况下实现 c + + 构造置换支持。 构造置换解决造成时在虚拟基中声明并在派生类中重写的虚拟函数的问题，在进一步的派生类的构造过程中从构造函数调用。  
  
 问题是，可能不正确传递的虚函数`this`指针因此到虚拟置换之间的差异的基类的类及其派生类到置换。 解决方案提供的 vtordisp 字段中，调用类的每个虚拟基的单个构造偏移量调整。  
  
 默认情况下，代码定义用户定义的构造函数和析构函数，并且还将重写虚拟基的虚函数时引入 vtordisp 字段。  
  
 这些选项会影响整个源文件。 使用[vtordisp](../../preprocessor/vtordisp.md)禁止显示，然后再重新启用 vtordisp 字段基于类的类。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)