---
title: "使 ATL 对象不可创建 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: b812c2d4bfeb0663d62051c05829f25dc7139faf
ms.lasthandoff: 02/24/2017

---
# <a name="making-an-atl-object-noncreatable"></a>使 ATL 对象不可创建
您可以更改基于 ATL 的 COM 对象的属性，以便客户端不能直接创建该对象。 在这种情况下，该对象将被另一个对象通过方法调用返回而不直接创建。  
  
### <a name="to-make-an-object-noncreatable"></a>若要使对象不可创建  
  
1.  删除[OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c)对象。 如果您想要不可创建，但要注册控件的对象，替换与 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](http://msdn.microsoft.com/library/abdc093c-6502-42de-8419-b7ebf45299d1)。  
  
2.  添加[noncreatable](../../windows/noncreatable.md)属性设为.idl 文件中的组件类。 例如:   
  
 ```  
 [  
    uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
 {  
 [default] interface IMyInterface;  
 }  
 ```  
  
## <a name="see-also"></a>另请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)


