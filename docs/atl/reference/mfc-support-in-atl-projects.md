---
title: "ATL 项目中的 MFC 支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 399f9fcea216adf5480bf38b8aba051c60eed496
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-support-in-atl-projects"></a>ATL 项目中的 MFC 支持
如果你选择**支持 MFC**在 ATL 项目向导中，则项目将声明为 MFC 应用程序对象 （类） 应用程序。 项目初始化 MFC 库并实例化类 (类*ProjName*)、 派生自[CWinApp](../../mfc/reference/cwinapp-class.md)。  
  
 此选项是仅适用于非特性化 ATL DLL 项目。  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
 
// Overrides  
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP() 
};  
 
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
 
CProjNameApp theApp;  
 
BOOL CProjNameApp::InitInstance()  
{  
    return CWinApp::InitInstance();

}  
 
int CProjNameApp::ExitInstance()  
{  
    return CWinApp::ExitInstance();

}  
```  
  
 你可以查看应用程序对象类及其`InitInstance`和`ExitInstance`类视图中的函数。  
  
## <a name="see-also"></a>请参阅  
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

