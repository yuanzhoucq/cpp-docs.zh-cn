---
title: "WRL 类库项目模板 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13fc476f696bdd2cb17ed58c496c63747db90322
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wrl-class-library-project-template"></a>WRL 类库项目模板
如果使用 Visual Studio 来编写的 Windows 运行时 c + + 模板库 (WRL) 项目，则将可以通过下载 WRL 类库项目模板极大地简化你的任务。  
  
> [!NOTE]
>  如果你必须手动更新现有项目的项目设置，请参阅[Dll (C + + /cli CX)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx)。  
  
## <a name="download-the-wrl-project-template"></a>下载 WRL 项目模板  
 Visual Studio 不提供针对 Windows 运行时 c + + 模板库项目模板。 下面介绍了如何下载与 Windows 运行时 c + + 模板库创建通用 Windows 平台应用程序的基本类库的项目模板。  
  
#### <a name="to-download-the-wrl-project-template"></a>下载 WRL 项目模板  
  
1.  在菜单栏上，选择**文件**，**新项目**。  
  
2.  在左窗格中**新项目**对话框中，选择**联机**，然后选择**模板**。  
  
3.  在**搜索联机模板**框右上角，类型中`WRL Class Library`。 当模板出现在搜索结果中时，选择**确定**按钮。  
  
4.  在**下载并安装**对话框中，如果你同意许可条款，请选择**安装**按钮。  
  
5.  在模板安装后，通过选择创建项目**文件**，**新项目**，然后选择`WRLClassLibrary`模板。 此项目将创建 DLL。  
  
## <a name="examples-that-use-the-project-template"></a>使用项目模板的示例  
 读取[演练： 创建基本 Windows 运行时组件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)有关的示例，使用此模板来创建 Windows 运行时组件。  
  
## <a name="what-the-project-template-provides"></a>项目模板提供的内容  
 项目模板将提供：  
  
-   将基础接口的 MIDL 特性声明为其类实现的 .idl 文件。 以下是一个示例。  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   定义类实现的 .cpp 文件。 以下是一个示例。  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     [RuntimeClass](../windows/runtimeclass-class.md)基类帮助管理模块中的所有对象的全局引用，并声明的方法[IUnknown](http://msdn.microsoft.com/en-us/33f1d79a-33fc-4ce5-a372-e08bda378332)和[IInspectable](http://msdn.microsoft.com/en-us/0657e51f-d4c0-46c6-927d-b01e54b6846c)接口。 [InspectableClass](../windows/inspectableclass-macro.md)宏实现`IUnknown`和`IInspectable`。 [ActivatableClass](../windows/activatableclass-macros.md)宏创建创建类的实例的类工厂。  
  
-   名为 module.cpp 的文件，其定义库导出 `DllMain`、`DllCanUnloadNow`、`DllGetActivationFactory` 和 `DllGetClassObject`。  
  
## <a name="see-also"></a>请参阅  
 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)