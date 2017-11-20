---
title: "-J (默认 char 类型是无符号) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs: C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a49220bf5ee4d990096140f4b2139992b03ad95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="j-default-char-type-is-unsigned"></a>/J（默认 char 类型是无符号的）
将默认 `char` 类型从 `signed char` 更改为 `unsigned char`，并且在将 `char` 类型扩展到 `int` 类型时，将对其进行零扩展。  
  
## <a name="syntax"></a>语法  
  
```  
/J  
```  
  
## <a name="remarks"></a>备注  
 如果`char`值显式声明为`signed`、 **/J**选项不影响它，且值为符号扩展时扩展到`int`类型。  
  
 **/J**选项定义`_CHAR_UNSIGNED`，与用于`#ifndef`LIMITS.h 文件定义的默认值的范围中`char`类型。  
  
 ANSI C 和 c + + 不需要的特定实现`char`类型。 当你正在使用最终将转换为非英语语言的字符数据时，此选项非常有用。  
  
> [!NOTE]
>  如果您将此编译器选项用于 ATL/MFC，则可能产生错误。 尽管您可以通过定义 `_ATL_ALLOW_CHAR_UNSIGNED` 禁用此错误，但此解决方法不受支持可能不会总是有用。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。  
  
2.  在项目中**属性页**对话框中，在左窗格中下**配置属性**，展开**C/c + +** ，然后选择**命令行**.  
  
3.  在**其他选项**窗格中，指定**/J**编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [使用项目属性](../../ide/working-with-project-properties.md)