---
title: "-链接 （将选项传递给链接器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /link
dev_langs: C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6732f5a2b144172939e23af4addb37b7605de11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="link-pass-options-to-linker"></a>/link（将选项传递到链接器）
将一个或多个链接器选项传递给链接器。  
  
## <a name="syntax"></a>语法  
  
```  
/link linkeroptions  
```  
  
## <a name="arguments"></a>自变量  
 `linkeroptions`  
 链接器选项或要传递到链接器的选项。  
  
## <a name="remarks"></a>备注  
 **/链接**选项和其链接器选项必须出现在任何文件的名称和 CL 选项之后。 则之间需要空间**/链接**和`linkeroptions`。 有关详细信息，请参阅[设置链接器选项](../../build/reference/setting-linker-options.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击链接器属性页。  
  
4.  修改一个或多个属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   不能以编程方式更改此编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)