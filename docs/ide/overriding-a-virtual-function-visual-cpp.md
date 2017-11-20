---
title: "重写虚函数 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.virtualfunc.override
dev_langs: C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 85e79cc21d745ad7f57c4c47b784e58359da6ef4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="overriding-a-virtual-function-visual-c"></a>重写虚函数 (Visual C++)
您可以重写基类从 Visual Studio 中定义的虚拟函数[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
### <a name="to-override-a-virtual-function-in-the-properties-window"></a>若要重写属性窗口中的虚函数  
  
1.  在类视图中，单击类。  
  
2.  在属性窗口中，单击**重写**按钮。  
  
    > [!NOTE]
    >  **重写**当在类视图或当您单击源窗口中选择类名时，按钮才可用。  
  
     左侧的列列出的虚拟函数。 如果虚拟函数的名称也会出现在右侧列中，则已实现重写。  
  
3.  如果函数具有不重写，然后单击在属性窗口来显示该函数的建议的名称右侧列中的单元格重写因为\<添加 >*FuncName*。  
  
4.  单击要添加函数的存根 （stub） 代码的建议的名称。  
  
5.  若要编辑重写函数，请双击类视图中函数的名称，然后编辑源窗口中的代码。  
  
 若要删除一个替代，单击右侧列中的重写函数名称，然后选择\<删除 >*FuncName*。 函数的代码注释掉。  
  
## <a name="see-also"></a>另请参阅  
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)   
 [MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)