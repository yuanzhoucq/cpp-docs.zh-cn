---
title: "WSADATA 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WSADATA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WSADATA 结构"
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# WSADATA 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`WSADATA` 结构存储 Windows 套接字调用返回的初始化信息对 `AfxSocketInit` 全局函数。  
  
## 语法  
  
```  
  
      struct WSAData {  
   WORD wVersion;  
   WORD wHighVersion;  
   char szDescription[WSADESCRIPTION_LEN+1];  
   char szSystemStatus[WSASYSSTATUS_LEN+1];  
   unsigned short iMaxSockets;  
   unsigned short iMaxUdpDg;  
   char FAR * lpVendorInfo;  
};  
```  
  
#### 参数  
 *wVersion*  
 Windows 套接规范的 Word 版本 Windows 套接字 DLL 希望调用方使用。  
  
 *wHighVersion*  
 此 DLL。支持 Windows 套接字规范的最高版本 \(也编码如上所述\)。  通常，这与 **wVersion**。  
  
 *szDescription*。  
 Windows 套接字 DLL 复制 Windows 套接字实现的 null 终止的 ASCII 字符串，包括提供商标识。  文本 \(长度为 256 个字符\) 可包含任何字符，但提供商警告控件包括控件和格式设置字符：最可能使用此应用程序将为显示它 \(可能会被截断\) 在状态消息。  
  
 *szSystemStatus*  
 Windows 套接字 DLL 复制相关状态或配置信息的 null 终止的 ASCII 字符串。  当信息可能是有用或对用户支撑杆，Windows 套接字 DLL 应使用该字段；不应视为 **szDescription** 字段用于的扩展。  
  
 *iMaxSockets*  
 一个过程可能打开套接字的最大数目。  Windows 套接字实现可以对所有进程的套接字提供分配一种全局池；或者，它会分配套接字的每个处理资源。  数字可以很好地反映 Windows 套接字 DLL 或网络软件配置的方式。  应用程序编写器可以使用此值作为一个粗暴表示 Windows 套接字实现是由应用程序可用。  例如，服务器可能检查 X Windows **iMaxSockets**，在首次启动：如果小于 8，应用程序将显示一条提示用户的错误消息重新配置网络软件。\(这是 **szSystemStatus** 文本可能使用的情况\)。显然不能保证某特定应用程序中实际 **iMaxSockets** 分配套接字，因为可以有正在使用其他 Windows 套接 Word 的应用程序。  
  
 *iMaxUdpDg*  
 大小在可由 Windows 套接字应用程序发送或接收的最大用户数据报协议 \(UDP\) \(UDP\) 数据报的字节。  如果实现不实现的限制，**iMaxUdpDg** 为零。  在 Berkeley 套接字实现的许多，有 8192 字节一个隐式限制。的如有必要，将的数据报 UDP \(\)  Windows 套接字实现可以实现根据片段组装重新分配缓冲区的限制的，例如。  **iMaxUdpDg** 由符合 CLS 的最小值，匹配的，适合的 Windows 套接字实现的是 512。  请注意，无论值 **iMaxUdpDg**，它是不妥当尝试发送大于最大网络上传输单元 \(MTU\) 的一广播数据报。\(Windows 套接字 API 未提供一种机制，MTU 查看，但不必须小于 512 字节。\)  
  
 *lpVendorInfo*  
 对卖方细节数据结构中较指针。  此结构的定义 \(如果提供\) 超出 Windows 套接字规范的范围。  
  
> [!NOTE]
>  在 MFC 中，`WSADATA` 结构由 `AfxSocketInit` 函数返回，在 `InitInstance` 函数调用。  如果您之后，需要使用其中的信息可以检索和存储结构以程序。  
  
## 要求  
 **标头：**winsock2.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../Topic/AfxSocketInit.md)