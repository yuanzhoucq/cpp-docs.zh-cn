---
title: "使 ATL 对象不可创建 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.objects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 不可创建的对象"
  - "不可创建的 ATL 对象"
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使 ATL 对象不可创建
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以更改基于 ATL 的 COM 对象的特性，使客户端不能直接创建该对象。  这种情况下，将通过另一对象上的方法调用返回对象，而不是直接创建对象。  
  
### 使对象不可创建  
  
1.  移除对象的 [OBJECT\_ENTRY\_AUTO](../Topic/OBJECT_ENTRY_AUTO.md)。  如果希望对象不可创建而控件能注册，则用 [OBJECT\_ENTRY\_NON\_CREATEABLE\_EX\_AUTO](../Topic/OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.md) 替换 OBJECT\_ENTRY\_AUTO。  
  
2.  在 .idl 文件中向 coclass 添加 [noncreatable](../../windows/noncreatable.md) 特性。  例如：  
  
    ```  
    [  
       uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),  
       helpstring("MyObject"),  
      noncreatable  
    ]  
    coclass MyObject  
    {  
       [default] interface IMyInterface;  
    }  
    ```  
  
## 请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)