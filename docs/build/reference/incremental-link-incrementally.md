---
title: "/INCREMENTAL（增量链接） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/incremental"
  - "VC.Project.VCLinkerTool.LinkIncremental"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INCREMENTAL 链接器选项"
  - "INCREMENTAL 链接器选项"
  - "-INCREMENTAL 链接器选项"
  - "增量链接"
  - "增量链接选项"
  - "LINK 工具 [C++], 用于完全链接的选项"
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /INCREMENTAL（增量链接）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/INCREMENTAL[:NO]  
```  
  
## 备注  
 控制链接器处理增量链接的方式。  
  
 默认情况下，链接器以增量模式运行。  若要重写默认增量链接，请指定 \/INCREMENTAL:NO。  
  
 增量链接的程序在功能上等效于非增量链接的程序。  但是，因为它是为后面的增量链接而准备的，所以增量链接的可执行 \(.exe\) 文件或动态链接库 \(DLL\)：  
  
-   大于非增量链接的程序，因为有代码和数据的填充。（填充使链接器可以增加函数和数据的大小而不用重新创建 .exe 文件。）  
  
-   可以包含跳转 thunk 以处理函数重定位到新地址。  
  
    > [!NOTE]
    >  为了确保最终发布版本不包含填充或 thunk，请非增量链接你的程序。  
  
 若要增量链接而不管默认值，请指定 \/INCREMENTAL。  选定此选项后，如果链接器无法增量链接，它就会发出警告，然后非增量链接程序。  某些选项和情况重写 \/INCREMENTAL。  
  
 大多数程序都可以增量链接。  但是，某些更改太大，还有某些选项与增量链接不兼容。  如果指定了以下任一选项，则 LINK 执行完全链接：  
  
-   未选定增量链接 \(\/INCREMENTAL:NO\)  
  
-   选定 \/OPT:REF  
  
-   选定 \/OPT:ICF  
  
-   选定 \/OPT:LBR  
  
-   选定 \/ORDER  
  
 指定 [\/DEBUG](../../build/reference/debug-generate-debug-info.md) 时隐式使用 \/INCREMENTAL。  
  
 此外，如果发生以下任何情况，则 LINK 执行完全链接：  
  
-   缺少增量状态 \(.ilk\) 文件。（LINK 将创建新的 .ilk 文件以为后面的增量链接作准备。）  
  
-   对 .ilk 文件没有写入权限。（LINK 忽略 .ilk 文件并进行非增量链接。）  
  
-   缺少 .exe 或 .dll 输出文件。  
  
-   更改了 .ilk、.exe 或 .dll 的时间戳。  
  
-   更改了 LINK 选项。  大多数 LINK 选项在各生成间更改时会导致完全链接。  
  
-   添加或省略了对象 \(.obj\) 文件。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“常规”**属性页。  
  
4.  修改**“启用增量链接”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)