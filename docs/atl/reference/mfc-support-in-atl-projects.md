---
title: ATL 项目中的 MFC 支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.addmfc
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d42afec863695b1cab05c2d3cf2f65f3d64a1507
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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

