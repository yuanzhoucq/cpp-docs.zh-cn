---
title: "MFC ActiveX 控件：使用常用属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLSID_CPicturePropPage"
  - "CLSID_CColorPropPage"
  - "CLSID_CFontPropPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLSID_CColorPropPage"
  - "CLSID_CFontPropPage"
  - "CLSID_CPicturePropPage"
  - "颜色常用属性页"
  - "字体, ActiveX 控件"
  - "MFC ActiveX 控件, 属性页"
  - "图片常用属性页"
  - "常用属性, 常用属性页"
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控件：使用常用属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论常用属性页对于 ActiveX 控件的可用性以及如何使用它们。  
  
 有关在 ActiveX 控件使用属性页的详细息，请参见下列文章：  
  
-   [MFC ActiveX 控件：属性页](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 为了使用 ActiveX 控件 MFC 提供了三个常用属性页：**CLSID\_CColorPropPage**、**CLSID\_CFontPropPage** 和 **CLSID\_CPicturePropPage**。  这些页面分别显示用户界面常用的颜色、字体和图片属性。  
  
 若要将这些属性页合并到控件中，添加其 ID 到代码中以初始化属性页 ID 的控件数组。  在下面的示例中，位于控件实现文件 \(.cpp\)，此代码初始化数组包含三个常用属性页、默认属性页 \(此示例中已命名的 `CMyPropPage` \):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/CPP/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 注意在 `BEGIN_PROPPAGEIDS` 宏中，属性页的计数是 4。  这表示支持 ActiveX 控件的属性页的数量。  
  
 在进行这些修改之后，请重新建立项目。  控件现在是具有字体、图片和颜色属性的属性页。  
  
> [!NOTE]
>  如果无法访问控件常用属性页，则可能是因为 MFC DLL \(MFCxx.DLL\) 未正确用当前操作系统注册。  在不同与当前运行的操作系统下，这通常因安装 Visual C\+\+引起。  
  
> [!TIP]
>  如果常用属性页不可见 \(请参见上述说明\)，请通过从完整路径名的命令行到 DLL运行 Regsvr32.exe 注册 DLL 。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：添加常用属性](../mfc/mfc-activex-controls-adding-stock-properties.md)