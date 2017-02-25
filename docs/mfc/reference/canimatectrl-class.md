---
title: "CAnimateCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimateCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "animation controls [C++], CAnimateCtrl class"
  - "CAnimateCtrl class"
  - "Windows common controls [C++], CAnimateCtrl class"
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CAnimateCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常用动画控件的功能。  
  
## 语法  
  
```  
  
class CAnimateCtrl : public CWnd  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimateCtrl::CAnimateCtrl](../Topic/CAnimateCtrl::CAnimateCtrl.md)|构造 `CAnimateCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimateCtrl::Close](../Topic/CAnimateCtrl::Close.md)|关闭AVI剪辑。|  
|[CAnimateCtrl::Create](../Topic/CAnimateCtrl::Create.md)|创建动画控件并将它附加到 `CAnimateCtrl` 对象。|  
|[CAnimateCtrl::CreateEx](../Topic/CAnimateCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建动画控件并将它附加到 `CAnimateCtrl` 对象。|  
|[CAnimateCtrl::IsPlaying](../Topic/CAnimateCtrl::IsPlaying.md)|指示音频视频交错的\(AVI\)是否剪辑使用。|  
|[CAnimateCtrl::Open](../Topic/CAnimateCtrl::Open.md)|打开AVI从文件剪切或资源和显示第一个帧。|  
|[CAnimateCtrl::Play](../Topic/CAnimateCtrl::Play.md)|播放AVI剪辑，不带声音。|  
|[CAnimateCtrl::Seek](../Topic/CAnimateCtrl::Seek.md)|显示AVI中的选定单个帧剪辑。|  
|[CAnimateCtrl::Stop](../Topic/CAnimateCtrl::Stop.md)|停止播放AVI剪辑。|  
  
## 备注  
 此控件\(并 `CAnimateCtrl` 选件类\)若要在运行Windows 95、Windows 98和Windows NT 3.51版下的程序可用和更高版本。  
  
 动画控件是显示了剪辑。AVI的矩形窗口\(交替的音频视频\)格式标准Windows视频\/音频格式。  AVI剪辑是一系列位图帧，如影片。  
  
 动画控件可以播放只简单的AVI剪辑。  具体而言，"剪切"由动画使用控件必须满足以下要求:  
  
-   必须正好包含一个视频流，它必须具有至少一个帧。  
  
-   可以最多具有文件中的两个流\(通常为另一个流，如果存在，是音频流，不过，动画控件忽略音频信息）。  
  
-   剪辑必须是未压缩或压缩与RLE8压缩。  
  
-   调色板更改不允许在视频流中。  
  
 可以添加AVI剪辑到您的应用程序作为AVI资源，也可能与您的应用程序作为单独的AVI文件。  
  
 由于您的线程继续执行，当AVI剪辑时，会显示一个常见用途动画控件是指示系统事件在较长操作时。  例如，在中，当系统搜索文件，查找对话框文件资源管理器将显示一个移动放大镜。  
  
 使用对话框编辑器，如果创建一 `CAnimateCtrl` 对象在对话框中或从对话框资源，将自动销毁它，当用户关闭对话框。  
  
 如果在中创建的一 `CAnimateCtrl` 对象，则可能需要销毁它。  如果在堆栈上创建 `CAnimateCtrl` 对象，自动销毁它。  使用 **new** 功能，如果要创建在堆的 `CAnimateCtrl` 对象，则必须对对象的 **delete** 销毁它。  如果从 `CAnimateCtrl` 派生新选件类并将该选件类的任何内存，请重写 `CAnimateCtrl` 析构函数进程分配。  
  
 有关使用 `CAnimateCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CAnimateCtrl](../../mfc/using-canimatectrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](../Topic/CAnimateCtrl::Create.md)   
 [ON\_CONTROL](../Topic/ON_CONTROL.md)