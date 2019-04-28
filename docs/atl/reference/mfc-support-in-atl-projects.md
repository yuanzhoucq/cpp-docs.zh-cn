---
title: ATL 项目中的 MFC 支持
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 0aece6805f1de987b0164f405e50b99fd706fef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275420"
---
# <a name="mfc-support-in-atl-projects"></a>ATL 项目中的 MFC 支持

如果选择**支持 MFC**在 ATL 项目向导中，则项目将声明为 MFC 应用程序对象 （类） 的应用程序。 初始化 MFC 库项目，并实例化一个类 (类*ProjName*) 派生自[CWinApp](../../mfc/reference/cwinapp-class.md)。

此选项是适用于非属性化 ATL DLL 项目。

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

您可以查看应用程序对象类及其`InitInstance`和`ExitInstance`类视图中的函数。

## <a name="see-also"></a>请参阅

[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)
