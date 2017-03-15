---
title: "MFC MBCS DLL 加载项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MBCS"
  - "MFC"
ms.assetid: bebec0ff-e019-42ca-b5df-8c218ac5b54a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# MFC MBCS DLL 加载项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual Studio 2015 中，用于多字节字符编码 \(MBCS\) 的 MFC 库包含在 Visual C\+\+ 安装组件中。 在 Visual Studio 安装程序中，Visual C\+\+ 和 MFC 是可选安装配置。 若要确保已安装 MFC，请在安装程序中选择“自定义”，并确保在“编程语言”下选择了“Visual C\+\+”和“用于 C\+\+ 的 Microsoft 基础类”。 如果已安装 Visual Studio，则尝试创建 MFC 项目时，系统将提示你安装 Visual C\+\+ 和\/或 MFC。  
  
 需要多字节 DLL 来在 Visual Studio 2015 中生成将“字符集”属性设置为“使用多字节字符集”或“未设置”的 MFC 项目。  
  
## 请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)