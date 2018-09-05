---
title: 使 ATL 对象不可创建 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a77ed656d39888e85e607ee4fdd96b384d0d250
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761451"
---
# <a name="making-an-atl-object-noncreatable"></a>使 ATL 对象不可创建

您可以更改基于 ATL 的 COM 对象的属性，以便客户端不能直接创建该对象。 在这种情况下，对象会被另一个对象上返回通过方法调用而不直接创建。

### <a name="to-make-an-object-noncreatable"></a>若要使对象不可创建

1. 删除[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)对象。 如果你想要注册的控件，但不可创建的对象，将替换为与 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)。

2. 添加[noncreatable](../../windows/noncreatable.md) .idl 文件中组件类的属性。 例如：

    ```  
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
    {  
        [default] interface IMyInterface;  
    }  
    ```

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
[Visual C++ 项目类型](../../ide/visual-cpp-project-types.md)   
[使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
[ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

