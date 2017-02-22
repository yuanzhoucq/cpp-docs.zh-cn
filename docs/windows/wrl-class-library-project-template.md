---
title: "WRL 类库项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# WRL 类库项目模板
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果使用 Visual Studio 编写 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\) 项目，可以通过下载 WRL 类库项目模板极大地简化任务。  
  
> [!NOTE]
>  如果必须手动更新现有的项目设置，请参见 [DLL \(C\+\+\/CX\)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx)。  
  
## 下载“VSIX 项目”模板。  
 Visual Studio 为 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 项目不提供一个模板。  如何下载这是创建 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用的基本类库与 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]的项目模板。  
  
#### 下载“VSIX 项目”模板。  
  
1.  在菜单栏上，选择**“文件”**，再选择**“新建项目”**。  
  
2.  在对话框的左窗格中，展开**“配置属性”**，然后选择**“常规”**，选择**模版**。  
  
3.  在 **搜索联机模板** 右上角框中，键入 `WRL 类库`。  当模板出现在搜索结果中，选择 **确定** 按钮。  
  
4.  在对话框中，**下载并安装**，如果您同意许可时间限制，请选择 **安装** 按钮。  
  
5.  在模板上安装后，请通过选择 **文件新建项目**，然后选择 `WRLClassLibrary`，创建项目模板。  创建DLL项目  
  
## 使用项目模板示例  
 将使用此模板创建 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件的示例。[演练：创建基本 Windows 运行时组件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
  
## 项目模板提供。  
 测试项目模板  
  
-   声明 MIDL 的 .idl 文件提供基本界面特性其类实现。  以下是一个示例。  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   定义了类实现的 .cpp 文件。  以下是一个示例。  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     [RuntimeClass](../windows/runtimeclass-class.md) 基类来帮助管理所有全局对象引用模块中以及 [IUnknown](http://msdn.microsoft.com/zh-cn/33f1d79a-33fc-4ce5-a372-e08bda378332) 声明和 [IInspectable](http://msdn.microsoft.com/zh-cn/0657e51f-d4c0-46c6-927d-b01e54b6846c) 接口的方法。  [InspectableClass](../windows/inspectableclass-macro.md) 宏实现 `IUnknown` 和 `IInspectable`。  [ActivatableClass](../windows/activatableclass-macros.md) 宏创建类实例的类工厂。  
  
-   文件中定义库导出了 `DllMain`、`DllCanUnloadNow`、`DllGetActivationFactory`和 `DllGetClassObject`的 module.cpp。  
  
## 请参阅  
 [Windows 运行时 C\+\+ 模板库 \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)