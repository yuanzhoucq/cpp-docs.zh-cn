---
title: "DEVNAMES 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEVNAMES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEVNAMES"
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# DEVNAMES 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`DEVNAMES` 结构包含标识驱动程序、设备和输出端口名称打印机的字符串。  
  
## 语法  
  
```  
  
      typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault;  
    /* driver, device, and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### 参数  
 *wDriverOffset*  
 \(\) 在输入\/输出字符指定偏移量。包含文件名的 null 终止的字符串 \(不带扩展名\) 的设备驱动程序。  在输入时，此字符串对话框中用于确定打印机最初显示。  
  
 *wDeviceOffset*  
 \(输入\/输出\)字符指定偏移量。包含设备名称的 null 终止的字符串 \(最多 32 字节 \(空\)。  此字符串绑定相同于 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) 结构的 **dmDeviceName** 成员中。  
  
 *wOutputOffset*  
 \(\) 在输入\/输出字符指定偏移量为 DOS 包含设备名称实际数据输出介质的 null 终止的字符串 \(输出 NANP 端口\)。  
  
 *默认*  
 指定在 `DEVNAMES` 配置包含的字符串标识是否默认打印机。  此字符串用于验证默认打印机未自上打印操作更改。  在输入时，如果 **DN\_DEFAULTPRN** 标志设置，`DEVNAMES` 结构的其他值是根据当前默认打印机进行。  如果其中任一字符串不匹配，则会显示警告消息通知用户的文档可能需要重新设置。  在输出时，**wDefault** 成员更改时，才设置打印对话框中显示，并且用户选择"确定"按钮。  如果默认打印机，选择 **DN\_DEFAULTPRN** 标志设置。  如果一台特定选择打印机，未设置任何标志。  此成员的其他 BITS 保留为内部使用过程由打印对话框。  
  
## 备注  
 **PrintDlg** 函数使用这些字符串初始化系统定义的打印对话框的成员。  当用户关闭对话框时，有关选择打印机的信息返回此结构。  
  
## 要求  
 **页眉：** commdlg.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../Topic/CPrintDialog::CreatePrinterDC.md)