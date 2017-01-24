---
title: "WeakRef 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakRef 类"
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示只能由 Windows 运行时而不是经典 COM 使用的*弱引用*。 弱引用表示可能可访问或可能不可访问的对象。  
  
## 语法  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## 备注  
 WeakRef 对象维护与对象相关联的*强引用*，该引用可以是有效的，也可以是无效的。 调用 As\(\) 或 AsIID\(\) 方法以获取强引用。 如果强引用有效，就可以访问关联的对象。 如果强引用无效 \(`nullptr`\)，不可访问关联的对象。  
  
 WeakRef 对象通常用于表示由外部线程或应用程序控制其是否存在的对象。 例如，通过文件对象的引用构造 WeakRef 对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。  
  
 请注意，Windows 10 SDK 中的 [As](../windows/weakref-as-method.md)、[AsIID](../windows/weakref-asiid-method.md) 和 [CopyTo](../windows/weakref-copyto-method.md) 方法中没有发生行为更改。 以前，在调用下列任一方法后，可以检查`nullptr` 的 WeakRef 来确定是否已成功获得强引用，代码如下：  
  
```cpp  
WeakRef wr; strongComptrRef.AsWeak(&wr); // Now suppose that the object strongComPtrRef points to no longer exists // and the following code tries to get a strong ref from the weak ref: ComPtr<ISomeInterface> strongRef; HRESULT hr = wr.As(&strongRef); // This check won't work with the Windows 10 SDK version of the library. // Use the HRESULT from previous As() call instead. if(wr == nullptr) { wprintf(L"Couldn’t get strong ref!"); }  
  
```  
  
 使用 Windows 10 SDK（或更高版本）时以上代码无效。 而会检查 As 或 AsIID 方法返回的 HRESULT，或检查为 `nullptr` 传入的指针。  
  
```cpp  
if (hr != S_OK) { wprintf(L"Couldn't get strong ref!"); }  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[WeakRef::WeakRef 构造函数](../windows/weakref-weakref-constructor.md)|初始化 WeakRef 类的新实例。|  
|[WeakRef::~WeakRef 析构函数](../windows/weakref-tilde-weakref-destructor.md)|取消初始化 WeakRef 类的当前实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[WeakRef::As 方法](../windows/weakref-as-method.md)|设置指定的 ComPtr 指针参数以表示指定接口。|  
|[WeakRef::AsIID 方法](../windows/weakref-asiid-method.md)|设置指定的 ComPtr 指针参数以表示指定的接口 ID。|  
|[WeakRef::CopyTo 方法](../windows/weakref-copyto-method.md)|如果可用，请为指定的指针变量分配一个指向接口的指针。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[WeakRef::operator& 运算符](../windows/weakref-operator-ampersand-operator.md)|返回表示当前 WeakRef 对象的 ComPtrRef 对象。|  
  
## 继承层次结构  
 `ComPtr`  
  
 `WeakRef`  
  
## 要求  
 **标头：**client.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)