---
title: "__cpuid, __cpuidex | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__cpuid_cpp"
  - "__cpuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__cpuid intrinsic"
  - "cpuid instruction"
  - "cpuid intrinsic"
ms.assetid: f8c344d3-91bf-405f-8622-cb0e337a6bdc
caps.latest.revision: 38
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 36
---
# __cpuid, __cpuidex
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成可在 x86 和 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 上使用的 `cpuid` 指令。  本指令可查询处理器，以获取有关支持的功能和 CPU 类型的信息。  
  
## 语法  
  
```  
void __cpuid(  
   int cpuInfo[4],  
   int function_id  
);  
  
void __cpuidex(  
   int cpuInfo[4],  
   int function_id,  
   int subfunction_id  
);  
```  
  
#### 参数  
 \[out\] `cpuInfo`  
 四个整数的数组，包含在 EAX、EBX、ECX 和 EDX 中返回的有关 CPU 支持的功能的信息。  
  
 \[in\] `function_id`  
 在 EAX 中传递的指定要检索的信息的代码。  
  
 \[in\] `subfunction_id`  
 在 ECX 中传递的指定要检索的信息的附加代码。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__cpuid`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__cpuidex`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此内部函数将存储由 `cpuInfo` 中的 `cpuid` 指令返回的支持功能和 CPU 信息，使用 EAX、EBX、ECX 和 EDX 寄存器值（按照这个顺序）填充的四个 32 位整数的数组。  返回的信息具有不同含义，具体取决于作为 `function_id` 参数传递的值。  随 `function_id` 的多个值返回的信息与处理器相关。  
  
 `__cpuid` 内部函数将在调用 `cpuid` 指令前清除 ECX 寄存器。  `__cpuidex` 内部函数可在 ECX 寄存器生成 `cpuid` 指令之前，将其值设置为 `subfunction_id`。  这使你能够收集有关该处理器的其他信息。  
  
 有关要使用的特定参数以及由 Intel 处理器上的这些内部函数返回的值的详细信息，请参阅 `cpuid` 指令文档，其位于 [Intel 64 and IA\-32 Architectures Software Developers Manual Volume 2:Instruction Set Reference](http://go.microsoft.com/fwlink/p/?LinkID=510021)（Intel 64 和 IA32 体系结构软件开发人员手册第 2 卷：指令集参考）和[Intel Architecture Instruction Set Extensions Programming Reference](http://go.microsoft.com/fwlink/p/?LinkID=506627)（Intel 体系结构指令集扩展编程参考）。  对于在 EAX 和 ECX 中传递的 `function_id` 和 `subfunction_id` 参数，Intel 文档将使用术语“leaf”和“subleaf”。  
  
 有关 AMD 处理器上要使用的特定参数和这些内部函数所返回的值的详细信息，请参阅 `cpuid` 指令文档，其位于 [AMD64 Architecture Programmer's Manual Volume 3:General\-Purpose and System Instructions](http://go.microsoft.com/fwlink/p/?LinkId=510023)（AMD64 体系结构编程人员手册第 3 卷：通用和系统指令）和 [Revision Guides](http://go.microsoft.com/fwlink/p/?LinkId=510023)（修订指南），了解特定处理器系列。  对于在 EAX 和 ECX 中传递的 `function_id` 和 `subfunction_id` 参数，AMD 文档将使用术语“function number”和“subfunction number”。  
  
 当 `function_id` 参数为 0 时，`cpuInfo[0]` 将返回由处理器支持的最高可用非扩展 `function_id`。  处理器制造商在 `cpuInfo[1]`、`cpuInfo[2]` 和 cpuInfo\[3\] 中进行编码。  
  
 支持在返回更高的 function\_id 值的 `cpuInfo` 结果中编码特定指令集扩展和 CPU 功能。  有关详细信息，请参阅上述链接的手册和以下示例代码。  
  
 某些处理器支持扩展函数 CPUID 信息。  如果支持此操作，则 0x80000000 中的 `function_id` 值可用于返回信息。  若要确定允许的有意义的最大值，请将 `function_id` 设置为 0x80000000。  支持扩展功能的 `function_id` 的最大值将被写入 `cpuInfo[0]`。  
  
## 示例  
 此示例显示了通过 `__cpuid` 和 `__cpuidex` 内部函数提供的一些信息。  此应用列出了受当前处理器支持的指令集扩展。  此输出显示了特定处理器的可能结果。  
  
```  
// InstructionSet.cpp   
// Compile by using: cl /EHsc /W4 InstructionSet.cpp  
// processor: x86, x64  
// Uses the __cpuid intrinsic to get information about   
// CPU extended instruction set support.  
  
#include <iostream>  
#include <vector>  
#include <bitset>  
#include <array>  
#include <string>  
#include <intrin.h>  
  
class InstructionSet  
{  
    // forward declarations  
    class InstructionSet_Internal;  
  
public:  
    // getters  
    static std::string Vendor(void) { return CPU_Rep.vendor_; }  
    static std::string Brand(void) { return CPU_Rep.brand_; }  
  
    static bool SSE3(void) { return CPU_Rep.f_1_ECX_[0]; }  
    static bool PCLMULQDQ(void) { return CPU_Rep.f_1_ECX_[1]; }  
    static bool MONITOR(void) { return CPU_Rep.f_1_ECX_[3]; }  
    static bool SSSE3(void) { return CPU_Rep.f_1_ECX_[9]; }  
    static bool FMA(void) { return CPU_Rep.f_1_ECX_[12]; }  
    static bool CMPXCHG16B(void) { return CPU_Rep.f_1_ECX_[13]; }  
    static bool SSE41(void) { return CPU_Rep.f_1_ECX_[19]; }  
    static bool SSE42(void) { return CPU_Rep.f_1_ECX_[20]; }  
    static bool MOVBE(void) { return CPU_Rep.f_1_ECX_[22]; }  
    static bool POPCNT(void) { return CPU_Rep.f_1_ECX_[23]; }  
    static bool AES(void) { return CPU_Rep.f_1_ECX_[25]; }  
    static bool XSAVE(void) { return CPU_Rep.f_1_ECX_[26]; }  
    static bool OSXSAVE(void) { return CPU_Rep.f_1_ECX_[27]; }  
    static bool AVX(void) { return CPU_Rep.f_1_ECX_[28]; }  
    static bool F16C(void) { return CPU_Rep.f_1_ECX_[29]; }  
    static bool RDRAND(void) { return CPU_Rep.f_1_ECX_[30]; }  
  
    static bool MSR(void) { return CPU_Rep.f_1_EDX_[5]; }  
    static bool CX8(void) { return CPU_Rep.f_1_EDX_[8]; }  
    static bool SEP(void) { return CPU_Rep.f_1_EDX_[11]; }  
    static bool CMOV(void) { return CPU_Rep.f_1_EDX_[15]; }  
    static bool CLFSH(void) { return CPU_Rep.f_1_EDX_[19]; }  
    static bool MMX(void) { return CPU_Rep.f_1_EDX_[23]; }  
    static bool FXSR(void) { return CPU_Rep.f_1_EDX_[24]; }  
    static bool SSE(void) { return CPU_Rep.f_1_EDX_[25]; }  
    static bool SSE2(void) { return CPU_Rep.f_1_EDX_[26]; }  
  
    static bool FSGSBASE(void) { return CPU_Rep.f_7_EBX_[0]; }  
    static bool BMI1(void) { return CPU_Rep.f_7_EBX_[3]; }  
    static bool HLE(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_7_EBX_[4]; }  
    static bool AVX2(void) { return CPU_Rep.f_7_EBX_[5]; }  
    static bool BMI2(void) { return CPU_Rep.f_7_EBX_[8]; }  
    static bool ERMS(void) { return CPU_Rep.f_7_EBX_[9]; }  
    static bool INVPCID(void) { return CPU_Rep.f_7_EBX_[10]; }  
    static bool RTM(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_7_EBX_[11]; }  
    static bool AVX512F(void) { return CPU_Rep.f_7_EBX_[16]; }  
    static bool RDSEED(void) { return CPU_Rep.f_7_EBX_[18]; }  
    static bool ADX(void) { return CPU_Rep.f_7_EBX_[19]; }  
    static bool AVX512PF(void) { return CPU_Rep.f_7_EBX_[26]; }  
    static bool AVX512ER(void) { return CPU_Rep.f_7_EBX_[27]; }  
    static bool AVX512CD(void) { return CPU_Rep.f_7_EBX_[28]; }  
    static bool SHA(void) { return CPU_Rep.f_7_EBX_[29]; }  
  
    static bool PREFETCHWT1(void) { return CPU_Rep.f_7_ECX_[0]; }  
  
    static bool LAHF(void) { return CPU_Rep.f_81_ECX_[0]; }  
    static bool LZCNT(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_ECX_[5]; }  
    static bool ABM(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[5]; }  
    static bool SSE4a(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[6]; }  
    static bool XOP(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[11]; }  
    static bool TBM(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[21]; }  
  
    static bool SYSCALL(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_EDX_[11]; }  
    static bool MMXEXT(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[22]; }  
    static bool RDTSCP(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_EDX_[27]; }  
    static bool _3DNOWEXT(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[30]; }  
    static bool _3DNOW(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[31]; }  
  
private:  
    static const InstructionSet_Internal CPU_Rep;  
  
    class InstructionSet_Internal  
    {  
    public:  
        InstructionSet_Internal()  
            : nIds_{ 0 },  
            nExIds_{ 0 },  
            isIntel_{ false },  
            isAMD_{ false },  
            f_1_ECX_{ 0 },  
            f_1_EDX_{ 0 },  
            f_7_EBX_{ 0 },  
            f_7_ECX_{ 0 },  
            f_81_ECX_{ 0 },  
            f_81_EDX_{ 0 },  
            data_{},  
            extdata_{}  
        {  
            //int cpuInfo[4] = {-1};  
            std::array<int, 4> cpui;  
  
            // Calling __cpuid with 0x0 as the function_id argument  
            // gets the number of the highest valid function ID.  
            __cpuid(cpui.data(), 0);  
            nIds_ = cpui[0];  
  
            for (int i = 0; i <= nIds_; ++i)  
            {  
                __cpuidex(cpui.data(), i, 0);  
                data_.push_back(cpui);  
            }  
  
            // Capture vendor string  
            char vendor[0x20];  
            memset(vendor, 0, sizeof(vendor));  
            *reinterpret_cast<int*>(vendor) = data_[0][1];  
            *reinterpret_cast<int*>(vendor + 4) = data_[0][3];  
            *reinterpret_cast<int*>(vendor + 8) = data_[0][2];  
            vendor_ = vendor;  
            if (vendor_ == "GenuineIntel")  
            {  
                isIntel_ = true;  
            }  
            else if (vendor_ == "AuthenticAMD")  
            {  
                isAMD_ = true;  
            }  
  
            // load bitset with flags for function 0x00000001  
            if (nIds_ >= 1)  
            {  
                f_1_ECX_ = data_[1][2];  
                f_1_EDX_ = data_[1][3];  
            }  
  
            // load bitset with flags for function 0x00000007  
            if (nIds_ >= 7)  
            {  
                f_7_EBX_ = data_[7][1];  
                f_7_ECX_ = data_[7][2];  
            }  
  
            // Calling __cpuid with 0x80000000 as the function_id argument  
            // gets the number of the highest valid extended ID.  
            __cpuid(cpui.data(), 0x80000000);  
            nExIds_ = cpui[0];  
  
            char brand[0x40];  
            memset(brand, 0, sizeof(brand));  
  
            for (int i = 0x80000000; i <= nExIds_; ++i)  
            {  
                __cpuidex(cpui.data(), i, 0);  
                extdata_.push_back(cpui);  
            }  
  
            // load bitset with flags for function 0x80000001  
            if (nExIds_ >= 0x80000001)  
            {  
                f_81_ECX_ = extdata_[1][2];  
                f_81_EDX_ = extdata_[1][3];  
            }  
  
            // Interpret CPU brand string if reported  
            if (nExIds_ >= 0x80000004)  
            {  
                memcpy(brand, extdata_[2].data(), sizeof(cpui));  
                memcpy(brand + 16, extdata_[3].data(), sizeof(cpui));  
                memcpy(brand + 32, extdata_[4].data(), sizeof(cpui));  
                brand_ = brand;  
            }  
        };  
  
        int nIds_;  
        int nExIds_;  
        std::string vendor_;  
        std::string brand_;  
        bool isIntel_;  
        bool isAMD_;  
        std::bitset<32> f_1_ECX_;  
        std::bitset<32> f_1_EDX_;  
        std::bitset<32> f_7_EBX_;  
        std::bitset<32> f_7_ECX_;  
        std::bitset<32> f_81_ECX_;  
        std::bitset<32> f_81_EDX_;  
        std::vector<std::array<int, 4>> data_;  
        std::vector<std::array<int, 4>> extdata_;  
    };  
};  
  
// Initialize static member data  
const InstructionSet::InstructionSet_Internal InstructionSet::CPU_Rep;  
  
// Print out supported instruction set extensions  
int main()  
{  
    auto& outstream = std::cout;  
  
    auto support_message = [&outstream](std::string isa_feature, bool is_supported) {  
        outstream << isa_feature << (is_supported ? " supported" : " not supported") << std::endl;  
    };  
  
    std::cout << InstructionSet::Vendor() << std::endl;  
    std::cout << InstructionSet::Brand() << std::endl;  
  
    support_message("3DNOW",       InstructionSet::_3DNOW());  
    support_message("3DNOWEXT",    InstructionSet::_3DNOWEXT());  
    support_message("ABM",         InstructionSet::ABM());  
    support_message("ADX",         InstructionSet::ADX());  
    support_message("AES",         InstructionSet::AES());  
    support_message("AVX",         InstructionSet::AVX());  
    support_message("AVX2",        InstructionSet::AVX2());  
    support_message("AVX512CD",    InstructionSet::AVX512CD());  
    support_message("AVX512ER",    InstructionSet::AVX512ER());  
    support_message("AVX512F",     InstructionSet::AVX512F());  
    support_message("AVX512PF",    InstructionSet::AVX512PF());  
    support_message("BMI1",        InstructionSet::BMI1());  
    support_message("BMI2",        InstructionSet::BMI2());  
    support_message("CLFSH",       InstructionSet::CLFSH());  
    support_message("CMPXCHG16B",  InstructionSet::CMPXCHG16B());  
    support_message("CX8",         InstructionSet::CX8());  
    support_message("ERMS",        InstructionSet::ERMS());  
    support_message("F16C",        InstructionSet::F16C());  
    support_message("FMA",         InstructionSet::FMA());  
    support_message("FSGSBASE",    InstructionSet::FSGSBASE());  
    support_message("FXSR",        InstructionSet::FXSR());  
    support_message("HLE",         InstructionSet::HLE());  
    support_message("INVPCID",     InstructionSet::INVPCID());  
    support_message("LAHF",        InstructionSet::LAHF());  
    support_message("LZCNT",       InstructionSet::LZCNT());  
    support_message("MMX",         InstructionSet::MMX());  
    support_message("MMXEXT",      InstructionSet::MMXEXT());  
    support_message("MONITOR",     InstructionSet::MONITOR());  
    support_message("MOVBE",       InstructionSet::MOVBE());  
    support_message("MSR",         InstructionSet::MSR());  
    support_message("OSXSAVE",     InstructionSet::OSXSAVE());  
    support_message("PCLMULQDQ",   InstructionSet::PCLMULQDQ());  
    support_message("POPCNT",      InstructionSet::POPCNT());  
    support_message("PREFETCHWT1", InstructionSet::PREFETCHWT1());  
    support_message("RDRAND",      InstructionSet::RDRAND());  
    support_message("RDSEED",      InstructionSet::RDSEED());  
    support_message("RDTSCP",      InstructionSet::RDTSCP());  
    support_message("RTM",         InstructionSet::RTM());  
    support_message("SEP",         InstructionSet::SEP());  
    support_message("SHA",         InstructionSet::SHA());  
    support_message("SSE",         InstructionSet::SSE());  
    support_message("SSE2",        InstructionSet::SSE2());  
    support_message("SSE3",        InstructionSet::SSE3());  
    support_message("SSE4.1",      InstructionSet::SSE41());  
    support_message("SSE4.2",      InstructionSet::SSE42());  
    support_message("SSE4a",       InstructionSet::SSE4a());  
    support_message("SSSE3",       InstructionSet::SSSE3());  
    support_message("SYSCALL",     InstructionSet::SYSCALL());  
    support_message("TBM",         InstructionSet::TBM());  
    support_message("XOP",         InstructionSet::XOP());  
    support_message("XSAVE",       InstructionSet::XSAVE());  
}  
```  
  
  **GenuineIntel**  
**Intel\(R\) Core\(TM\) i5\-2500 CPU @ 3.30GHz**  
**不支持 3DNOW**  
**不支持 3DNOWEXT**  
**不支持 ABM**  
**不支持 ADX**  
**支持 AES**  
**支持 AVX**  
**不支持 AVX2**  
**不支持 AVX512CD**  
**不支持 AVX512ER**  
**不支持 AVX512F**  
**不支持 AVX512PF**  
**不支持 BMI1**  
**不支持 BMI2**  
**支持 CLFSH**  
**支持 CMPXCHG16B**  
**支持 CX8**  
**不支持 ERMS**  
**不支持 F16C**  
**不支持 FMA**  
**不支持 FSGSBASE**  
**支持 FXSR**  
**不支持 HLE**  
**不支持 INVPCID**  
**支持 LAHF**  
**不支持 LZCNT**  
**支持 MMX**  
**不支持 MMXEXT**  
**不支持 MONITOR**  
**不支持 MOVBE**  
**支持 MSR**  
**支持 OSXSAVE**  
**支持 PCLMULQDQ**  
**支持 POPCNT**  
**不支持 PREFETCHWT1**  
**不支持 RDRAND**  
**不支持 RDSEED**  
**支持 RDTSCP**  
**不支持 RTM**  
**支持 SEP**  
**不支持 SHA**  
**支持 SSE**  
**支持 SSE2**  
**支持 SSE3**  
**支持 SSE4.1**  
**支持 SSE4.2**  
**不支持 SSE4a**  
**支持 SSSE3**  
**支持 SYSCALL**  
**不支持 TBM**  
**不支持 XOP**  
**支持 XSAVE**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)