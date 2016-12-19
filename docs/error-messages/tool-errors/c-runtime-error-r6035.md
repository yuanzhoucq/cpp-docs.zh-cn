---
title: "C 运行时错误 R6035 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6035"
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 运行时错误 R6035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft Visual C\+\+ 运行库，错误 R6035 \- 在依赖模块的全局安全 Cookie 的函数处于活动状态的情况下，此应用程序中的模块初始化该安全 Cookie。以前调用过 \_\_security\_init\_cookie。  
  
 在首次使用全局安全 Cookie 之前，必须调用 [\_\_security\_init\_cookie](../../c-runtime-library/reference/security-init-cookie.md)。  
  
 在用 [\/GS（缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md) 编译的代码和使用结构化异常处理的代码中，全局安全 Cookie 用于缓冲区溢出保护。  实质上，在进入溢出保护的函数时，会将该 Cookie 放在堆栈上；在退出该函数时，会将堆栈上的值与全局 Cookie 进行比较。  如果它们之间有任何区别，则指示缓冲区溢出已经发生并将导致立即终止程序。  
  
 错误 R6035 指示在进入受保护的函数后，已经对 `__security_init_cookie` 进行了调用。  如果要继续执行，则会检测到虚假的缓冲区溢出，因为堆栈上的 Cookie 将不再与全局 Cookie 相匹配。  
  
 请考虑下面的 DLL 示例。  DLL 入口点通过链接器的 [\/ENTRY（入口点符号）](../../build/reference/entry-entry-point-symbol.md) 选项设置为 DllEntryPoint。  这会跳过 CRT 的初始化（该初始化通常初始化全局安全 Cookie），因此 DLL 本身必须调用 `__security_init_cookie`。  
  
```  
// Wrong way to call __security_init_cookie  
DllEntryPoint(...) {  
   DllInitialize();  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
  
void DllInitialize() {  
   __security_init_cookie();  
}  
```  
  
 此示例将生成错误 R6035，因为 DllEntryPoint 使用结构化异常处理，从而使用安全 Cookie 检测缓冲区溢出。  在调用 DllInitialize 时，全局安全 Cookie 已经放在堆栈上。  
  
 下面的示例将演示正确的方法：  
  
```  
// Correct way to call __security_init_cookie  
DllEntryPoint(...) {  
   __security_init_cookie();  
   DllEntryHelper();  
}  
  
void DllEntryHelper() {  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
```  
  
 在这种情况下，没有防止 DllEntryPoint 出现缓冲区溢出（DllEntryPoint 没有本地字符串缓冲区，也不使用结构化异常处理）；因此 DllEntryPoint 可以安全地调用 `__security_init_cookie`。  DllEntryPoint 随后调用受到保护的 Helper 函数。  
  
> [!NOTE]
>  错误信息 R6035 仅由 x86 调试 CRT 生成，而且仅用于结构化异常处理，但是该情况是所有平台上的错误，并且适用于各种形式的异常处理，如 C\+\+ EH。  
  
## 请参阅  
 [深入的编译器安全检查](http://go.microsoft.com/fwlink/?linkid=7260)