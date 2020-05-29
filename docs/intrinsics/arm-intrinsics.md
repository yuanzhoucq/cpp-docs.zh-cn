---
title: ARM 内部函数
description: Microsoft C++编译器在 Visual Studio 中支持的 ARM64 内部函数的参考列表。
ms.date: 09/02/2019
f1_keywords:
- arm_neon/vsetq_lane_p8
- armintr/_arm_uxtb
- arm_neon/vld4_lane_p8
- arm_neon/vrshrn_n_s64
- arm_neon/vsli_n_u32
- arm_neon/vsraq_n_u16
- arm_neon/vcgt_f32
- armintr/__iso_volatile_store32
- arm_neon/vceqq_f32
- armintr/_arm_smlal
- arm_neon/vmull_n_s32
- arm_neon/vmax_s8
- arm_neon/vmvn_u32
- arm_neon/vrshl_u32
- arm_neon/int32x2_t
- arm_neon/vdupq_n_p8
- arm_neon/vpmax_u16
- arm_neon/vtrnq_s32
- arm_neon/vset_lane_f32
- arm_neon/vrev64_s8
- arm_neon/vtrnq_p8
- arm_neon/vqshlq_u64
- arm_neon/vld1q_dup_s64
- arm_neon/vmovq_n_u64
- arm_neon/vqshrn_n_u16
- arm_neon/vhadd_s32
- arm_neon/vrhaddq_u32
- arm_neon/vst1q_p8
- arm_neon/vshrn_n_s16
- arm_neon/vget_high_f32
- arm_neon/vuzpq_s16
- arm_neon/vand_u16
- arm_neon/vmulq_s32
- arm_neon/vrsraq_n_s64
- arm_neon/vceqq_s8
- arm_neon/uint64x1x3_t
- arm_neon/veor_u32
- armintr/_arm_pkhtb
- arm_neon/vorrq_u16
- arm_neon/vpaddl_s8
- arm_neon/vmla_n_s16
- arm_neon/vqdmlal_lane_s32
- arm_neon/vshlq_n_u8
- arm_neon/vst2_lane_p8
- arm_neon/vld3q_u16
- arm_neon/vandq_u8
- arm_neon/vst1_u64
- arm_neon/vaddq_s64
- arm_neon/vuzpq_u32
- arm_neon/vld3_lane_p8
- arm_neon/vminq_s32
- arm_neon/vabd_u16
- arm_neon/vdup_n_u32
- arm_neon/vmul_p8
- arm_neon/vsra_n_u16
- arm_neon/vst3q_u16
- arm_neon/int32x2x3_t
- arm_neon/vld2_dup_u16
- arm_neon/vrhaddq_u8
- arm_neon/vhadd_u8
- arm_neon/vgetq_lane_s32
- arm_neon/vcleq_u16
- arm_neon/vabdq_s8
- arm_neon/vrev16q_u8
- arm_neon/vqshlu_n_s64
- arm_neon/vcvt_n_s32_f32
- arm_neon/vqrshrn_n_s64
- arm_neon/vst1q_p16
- arm_neon/vgetq_lane_s16
- arm_neon/vtstq_u32
- arm_neon/vmlsl_n_s16
- arm_neon/vcge_s8
- arm_neon/vshr_n_s16
- armintr/_arm_rbit
- arm_neon/vmls_u32
- arm_neon/vmls_lane_u32
- arm_neon/vcvtq_n_s32_f32
- arm_neon/vqshl_n_s8
- arm_neon/vst1q_s16
- armintr/__emit
- arm_neon/vshlq_s64
- arm_neon/vuzp_s8
- arm_neon/vld1q_lane_s64
- arm_neon/veorq_s32
- arm_neon/vaddq_u64
- arm_neon/vceq_s32
- arm_neon/vmovn_u16
- arm_neon/vabal_s8
- arm_neon/vabsq_f32
- armintr/_arm_smuad
- arm_neon/veor_u8
- arm_neon/int16x4_t
- arm_neon/vsraq_n_s16
- arm_neon/vshlq_s8
- arm_neon/vcreate_u32
- arm_neon/vzipq_s8
- arm_neon/vst3q_u8
- arm_neon/int64x1x4_t
- armintr/__iso_volatile_store16
- arm_neon/vst4_lane_p16
- arm_neon/vld1_dup_p16
- arm_neon/vhadd_s16
- arm_neon/vtbl2_s8
- arm_neon/veorq_u32
- arm_neon/vqdmlal_lane_s16
- arm_neon/vrsra_n_u8
- arm_neon/vbslq_u16
- arm_neon/vget_low_s64
- arm_neon/vceq_u16
- arm_neon/vdupq_lane_u32
- arm_neon/vabdl_u32
- arm_neon/vmlal_s32
- arm_neon/vst1_lane_u8
- arm_neon/vld4q_f16
- arm_neon/vqdmlsl_s32
- arm_neon/vqrdmulh_s32
- arm_neon/vqrshl_u8
- arm_neon/uint32x4x4_t
- arm_neon/vabaq_u16
- arm_neon/vcnt_p8
- arm_neon/vld3q_s16
- arm_neon/vshl_n_u32
- arm_neon/vrev64q_u16
- arm_neon/vextq_s64
- arm_neon/vhsubq_s8
- arm_neon/vld2_dup_u8
- arm_neon/vst3_s16
- arm_neon/vorn_u16
- arm_neon/vst4_f16
- arm_neon/vpadalq_u8
- armintr/__iso_volatile_load8
- arm_neon/vmovl_u16
- arm_neon/vld4q_u32
- arm_neon/vcgt_u32
- arm_neon/vmlaq_n_u32
- arm_neon/vrsra_n_u64
- arm_neon/vst4_s8
- arm_neon/vcvtq_n_f32_u32
- arm_neon/vst2q_u16
- arm_neon/vqshrn_n_s16
- arm_neon/vld4_s16
- arm_neon/uint16x8x4_t
- arm_neon/vrsqrte_u32
- arm_neon/vcltq_s8
- arm_neon/vst3_u16
- arm_neon/vst2_f32
- arm_neon/vld2_u64
- arm_neon/vst1_u16
- arm_neon/vmls_s16
- arm_neon/vqrshlq_s32
- arm_neon/vqdmull_s16
- arm_neon/vld2_lane_p16
- arm_neon/vpaddlq_u8
- arm_neon/vcvt_n_f32_u32
- arm_neon/vcgtq_u8
- arm_neon/vshl_s32
- arm_neon/vtbx3_p8
- arm_neon/vld3_dup_s32
- arm_neon/int16x4x3_t
- arm_neon/vcale_f32
- arm_neon/vqabsq_s32
- arm_neon/vmulq_u16
- arm_neon/vst1_s8
- arm_neon/vclt_u8
- armintr/_arm_sxtb16
- arm_neon/vshr_n_s8
- arm_neon/vst1_lane_f16
- arm_neon/vorn_s64
- armintr/_arm_usub8
- arm_neon/vst4_lane_f32
- arm_neon/vmls_lane_u16
- arm_neon/vpaddl_u32
- arm_neon/vdup_lane_u64
- arm_neon/vsri_n_p16
- arm_neon/vqrshlq_u64
- arm_neon/vclz_s16
- arm_neon/vsra_n_u32
- arm_neon/vabaq_s8
- arm_neon/vst2_lane_s8
- arm_neon/vcvt_n_u32_f32
- arm_neon/vst3_u32
- arm_neon/vcvtq_f32_u32
- arm_neon/vraddhn_s64
- armintr/_arm_uqsax
- arm_neon/vshl_u8
- armintr/_arm_uqadd16
- arm_neon/vrsra_n_u16
- arm_neon/vrshl_u64
- arm_neon/int32x4x3_t
- arm_neon/vmull_u8
- arm_neon/vcombine_u64
- arm_neon/vmull_u16
- arm_neon/vld1_dup_s8
- armintr/_CountLeadingSigns64
- arm_neon/vqshlq_n_s32
- arm_neon/vrecpe_f32
- arm_neon/vsri_n_u32
- arm_neon/vrsraq_n_s8
- arm_neon/vsetq_lane_s16
- arm_neon/vget_high_u32
- arm_neon/vmlal_u32
- arm_neon/vdupq_lane_s16
- arm_neon/vsubq_u64
- arm_neon/vext_p8
- arm_neon/vshl_u16
- arm_neon/vmls_n_u16
- arm_neon/vmull_s16
- arm_neon/vmovq_n_s64
- arm_neon/vaddq_f32
- arm_neon/vshl_n_s16
- arm_neon/vext_p16
- arm_neon/vextq_u32
- arm_neon/vld1_p8
- arm_neon/veor_s32
- arm_neon/int16x8x4_t
- arm_neon/vst1q_u16
- arm_neon/vzipq_p8
- arm_neon/int32x4x4_t
- arm_neon/vqdmulhq_lane_s32
- arm_neon/vst3_lane_u32
- arm_neon/vhsubq_s32
- armintr/__static_assert
- arm_neon/vst3q_lane_u16
- arm_neon/vpmin_u32
- arm_neon/vrev64q_p16
- arm_neon/vcleq_f32
- arm_neon/vhsub_u16
- arm_neon/vld2_lane_s32
- arm_neon/vmlsl_s32
- armintr/_arm_rev
- arm_neon/vcgeq_s16
- arm_neon/vmulq_s8
- arm_neon/vsri_n_s8
- arm_neon/vpadd_f32
- arm_neon/vld1q_lane_f16
- arm_neon/vmls_u16
- arm_neon/vld1_lane_f32
- arm_neon/vmlaq_lane_s16
- arm_neon/vqadd_u32
- arm_neon/vmul_n_s32
- arm_neon/vld1q_dup_p8
- arm_neon/vtrnq_s8
- arm_neon/vbslq_p8
- arm_neon/vget_lane_s8
- arm_neon/vext_u16
- arm_neon/vsubq_s16
- arm_neon/vld4_lane_s8
- arm_neon/uint32x2x2_t
- arm_neon/vdup_n_s8
- arm_neon/vld4_lane_u16
- arm_neon/vmovq_n_s16
- arm_neon/vst4q_s32
- arm_neon/vst2q_f16
- arm_neon/vbslq_s16
- arm_neon/vand_u64
- arm_neon/poly16_t
- arm_neon/vaba_u16
- arm_neon/vqshlq_s64
- armintr/_arm_uxth
- arm_neon/vst2_lane_s16
- arm_neon/vand_u8
- arm_neon/int8x16x3_t
- arm_neon/vrev64_u16
- arm_neon/vld2_lane_s16
- arm_neon/vabaq_s16
- arm_neon/vsli_n_u8
- arm_neon/vsraq_n_u64
- arm_neon/vmlsl_s16
- arm_neon/vmovn_u64
- arm_neon/vld4_f32
- arm_neon/vst2q_f32
- arm_neon/vtbx3_u8
- arm_neon/vcombine_s8
- arm_neon/vqdmulhq_s32
- arm_neon/vgetq_lane_p8
- armintr/_arm_smusd
- arm_neon/vpmax_u32
- arm_neon/vceq_f32
- arm_neon/vsri_n_p8
- arm_neon/vhsubq_u8
- arm_neon/vuzp_s16
- arm_neon/uint32x2x4_t
- arm_neon/vst4_lane_s32
- arm_neon/vsli_n_p8
- arm_neon/vld3_lane_f16
- arm_neon/vbic_u64
- arm_neon/vmlal_u16
- arm_neon/vmvn_s8
- arm_neon/vtstq_s8
- arm_neon/vmaxq_s32
- arm_neon/vqmovn_u64
- armintr/_arm_ssax
- arm_neon/vext_u32
- arm_neon/vld1_dup_u64
- arm_neon/vmlal_n_s16
- armintr/_arm_smulbb
- arm_neon/vqrdmulhq_lane_s16
- arm_neon/vdup_n_p8
- arm_neon/vaba_s8
- arm_neon/vrshrq_n_s32
- arm_neon/vmvnq_s32
- arm_neon/vpadal_s32
- arm_neon/vqshl_s16
- arm_neon/vtrn_p8
- arm_neon/vzip_s16
- arm_neon/vcge_f32
- armintr/_arm_sxtab16
- arm_neon/vst1q_lane_u64
- arm_neon/vqrshlq_u16
- arm_neon/int8x8_t
- arm_neon/vorr_u8
- arm_neon/vrev64_f32
- arm_neon/vpaddlq_s16
- arm_neon/vdupq_lane_u64
- arm_neon/vcltq_u16
- arm_neon/vst3_lane_f32
- arm_neon/vld2_dup_f32
- armintr/_arm_smmul
- arm_neon/vbsl_s16
- arm_neon/vld1_lane_u8
- arm_neon/vld2q_lane_u16
- arm_neon/vqshlu_n_s32
- armintr/_arm_smlalbt
- arm_neon/vmla_s8
- arm_neon/vsli_n_p16
- arm_neon/vmla_u8
- arm_neon/vqaddq_s16
- arm_neon/vld3_p16
- arm_neon/uint64x2x4_t
- arm_neon/vcnt_u8
- arm_neon/vcltq_u8
- arm_neon/vtbx1_p8
- arm_neon/vrev32q_u16
- arm_neon/vld1_lane_u16
- arm_neon/vqadd_s16
- arm_neon/vcnt_s8
- armintr/_MulUnsignedHigh
- arm_neon/vsliq_n_u8
- arm_neon/vpmin_s16
- armintr/__iso_volatile_load16
- arm_neon/vst2_lane_f32
- arm_neon/vqsubq_s32
- arm_neon/vqshl_s32
- arm_neon/vsraq_n_u32
- arm_neon/vcreate_s32
- arm_neon/vld3q_lane_u32
- arm_neon/vaddq_u16
- arm_neon/vand_s32
- arm_neon/vbicq_s32
- armintr/_arm_smulbt
- arm_neon/vrsra_n_s8
- arm_neon/vshrq_n_u32
- arm_neon/vld4_f16
- arm_neon/vcagtq_f32
- arm_neon/vaddw_u32
- armintr/_arm_uxtah
- arm_neon/vtstq_u8
- arm_neon/vld1_dup_u16
- arm_neon/int16x4x4_t
- arm_neon/vqshluq_n_s8
- arm_neon/vqdmulhq_n_s32
- arm_neon/vst1_s64
- arm_neon/vrsubhn_u16
- arm_neon/vld4_dup_p16
- arm_neon/vmlaq_s32
- arm_neon/vnegq_s32
- arm_neon/vst2q_u8
- arm_neon/vget_low_s32
- arm_neon/vorn_u32
- arm_neon/vld1q_s8
- arm_neon/vandq_s64
- arm_neon/vmvn_p8
- arm_neon/vabdl_s16
- arm_neon/vqshl_u32
- arm_neon/vld3_dup_u16
- arm_neon/vmov_n_f32
- arm_neon/vcvt_f32_u32
- arm_neon/vrhadd_s8
- arm_neon/vpadal_u32
- armintr/_arm_ubfx
- arm_neon/vcgt_s8
- arm_neon/vget_lane_f32
- arm_neon/vcge_s16
- arm_neon/vmov_n_s64
- arm_neon/vmulq_n_f32
- arm_neon/vpadalq_u32
- armintr/_arm_smlaldx
- arm_neon/vtst_u16
- arm_neon/vmls_n_s16
- arm_neon/vcombine_f32
- arm_neon/vld1q_p16
- armintr/_arm_ssat
- arm_neon/vextq_s8
- arm_neon/vmax_u32
- arm_neon/vqsubq_s64
- arm_neon/vcltq_s16
- arm_neon/vst2q_s8
- arm_neon/vpmax_u8
- arm_neon/vld4_dup_p8
- arm_neon/vrshr_n_u64
- arm_neon/vqrshrun_n_s16
- arm_neon/vget_low_u64
- arm_neon/vst2q_s32
- arm_neon/vst4_s32
- arm_neon/vrshrq_n_u8
- arm_neon/vdupq_n_u64
- arm_neon/vsriq_n_u8
- arm_neon/vdupq_lane_u8
- arm_neon/vsriq_n_s64
- arm_neon/vget_low_u8
- arm_neon/vst1_lane_p16
- arm_neon/vld1q_lane_u8
- arm_neon/vcgt_s32
- arm_neon/vst1_lane_u32
- arm_neon/vzipq_p16
- arm_neon/vmvn_u16
- arm_neon/vld1q_lane_u16
- armintr/_MoveToCoprocessor64
- arm_neon/vdup_n_u16
- arm_neon/vzipq_f32
- arm_neon/vshl_s16
- arm_neon/vmlaq_n_s16
- arm_neon/vget_lane_s64
- arm_neon/vld1q_lane_f32
- arm_neon/vnegq_s16
- armintr/_arm_usax
- arm_neon/vabd_s16
- arm_neon/vmovq_n_u32
- arm_neon/vshlq_n_u16
- armintr/_CountLeadingSigns
- arm_neon/vld3q_f16
- arm_neon/vceqq_u32
- arm_neon/int8x8x2_t
- arm_neon/vst2_s64
- arm_neon/vst4q_lane_s16
- arm_neon/vorn_s32
- arm_neon/vcle_f32
- arm_neon/vld1_p16
- arm_neon/vtrn_u32
- arm_neon/vbsl_s32
- arm_neon/float32x2_t
- arm_neon/vmvn_s32
- arm_neon/vqdmlsl_lane_s16
- arm_neon/vtbl3_s8
- arm_neon/vsra_n_u8
- arm_neon/vcvtq_u32_f32
- arm_neon/vst1_p8
- arm_neon/vrev64_p16
- armintr/__ldrexd
- arm_neon/vcgeq_u8
- arm_neon/vmlal_n_s32
- arm_neon/vst1q_lane_p8
- arm_neon/vpadalq_s32
- arm_neon/vtstq_p8
- arm_neon/vld4_lane_u8
- armintr/_arm_ssub16
- arm_neon/vpaddlq_u16
- armintr/_arm_udiv
- arm_neon/vld1_lane_p8
- arm_neon/vst1q_u32
- arm_neon/vld1_f32
- arm_neon/uint64x2x2_t
- arm_neon/vqsubq_u64
- arm_neon/vld4q_s32
- arm_neon/vceq_s16
- arm_neon/vst3_s64
- arm_neon/vext_s8
- armintr/_arm_smlsd
- arm_neon/vpadal_s16
- arm_neon/vbic_s32
- arm_neon/vld1_dup_u8
- arm_neon/vclt_f32
- arm_neon/vrev64_s16
- arm_neon/vrshlq_s64
- arm_neon/vdupq_n_s64
- arm_neon/vuzp_p16
- arm_neon/vld3_dup_p16
- arm_neon/vcreate_s8
- armintr/_arm_smlatt
- arm_neon/vtst_s32
- arm_neon/vshrq_n_s64
- arm_neon/vqshlq_n_s64
- arm_neon/vqshlu_n_s16
- arm_neon/vcleq_s16
- arm_neon/vmull_lane_s16
- arm_neon/int32x4_t
- arm_neon/vqadd_s8
- arm_neon/vld2q_f16
- arm_neon/vld2q_lane_p16
- arm_neon/vadd_u32
- arm_neon/vcntq_u8
- arm_neon/vst1_f32
- arm_neon/vmaxq_u32
- arm_neon/vsub_u64
- arm_neon/vsubl_s32
- arm_neon/poly16x4_t
- arm_neon/vgetq_lane_u16
- arm_neon/vdup_lane_s32
- arm_neon/vrhadd_s32
- arm_neon/veorq_u8
- arm_neon/vclzq_s8
- arm_neon/vsliq_n_s64
- arm_neon/vpadalq_s16
- arm_neon/vmla_n_f32
- arm_neon/vcgt_u16
- armintr/_arm_usada8
- arm_neon/vabd_u32
- arm_neon/vgetq_lane_s8
- arm_neon/vqshlq_n_u64
- arm_neon/vabaq_u32
- armintr/_arm_uhsax
- arm_neon/vmulq_f32
- arm_neon/vld3_dup_s16
- arm_neon/vst3_f16
- arm_neon/vrshrq_n_s64
- armintr/__rdpmccntr64
- arm_neon/vclsq_s32
- arm_neon/vmax_u16
- arm_neon/vmvnq_p8
- arm_neon/veor_u16
- arm_neon/vqshrn_n_u32
- arm_neon/vextq_u64
- arm_neon/vld1q_f32
- arm_neon/vget_low_u32
- arm_neon/vhaddq_s32
- arm_neon/vminq_u16
- arm_neon/vqrdmulhq_lane_s32
- arm_neon/vmla_s16
- arm_neon/vadd_s16
- arm_neon/vbsl_u16
- arm_neon/vhsub_s8
- arm_neon/vld4q_lane_p16
- arm_neon/vld1_s16
- arm_neon/vst2q_lane_p16
- arm_neon/vld2_dup_s8
- arm_neon/vst3q_s16
- arm_neon/vcgeq_u32
- arm_neon/vabdq_s16
- arm_neon/vrhadd_u16
- arm_neon/vqshlq_n_u32
- arm_neon/vst4q_lane_u32
- arm_neon/vrsraq_n_u64
- arm_neon/vmlsq_n_s32
- arm_neon/vld4_u8
- arm_neon/vld2_f16
- arm_neon/vqshlq_u8
- arm_neon/vorrq_u64
- arm_neon/vmin_u16
- arm_neon/vext_u8
- arm_neon/vpaddl_s32
- arm_neon/vshlq_u64
- arm_neon/vst2q_lane_f16
- armintr/_arm_sbfx
- arm_neon/vld3_dup_f16
- armintr/_arm_uhasx
- arm_neon/vst2_lane_u8
- armintr/_arm_smultb
- arm_neon/vdup_n_p16
- arm_neon/vtrnq_u32
- arm_neon/vrshlq_u8
- arm_neon/vld4_lane_p16
- arm_neon/vsraq_n_s32
- arm_neon/vclt_s16
- arm_neon/vzip_u8
- arm_neon/vld3_lane_s16
- arm_neon/vceqq_s32
- arm_neon/vld3_dup_f32
- arm_neon/vld4q_lane_s32
- arm_neon/poly8x16x4_t
- arm_neon/uint64x1x2_t
- arm_neon/vqdmlal_n_s16
- arm_neon/vld2_dup_f16
- arm_neon/vshrq_n_s32
- arm_neon/vcleq_s8
- arm_neon/vld3_s32
- arm_neon/vqrshlq_s64
- arm_neon/vbsl_f32
- arm_neon/vext_s64
- arm_neon/vabaq_s32
- arm_neon/vmulq_s16
- arm_neon/vld3_lane_u16
- arm_neon/vld3q_lane_u16
- armintr/_arm_smlaltt
- arm_neon/poly8x8x2_t
- arm_neon/vst3q_u32
- armintr/_arm_smlsdx
- arm_neon/vqrshl_s64
- arm_neon/vextq_p8
- armintr/_arm_uhsub16
- arm_neon/vld3q_p8
- armintr/_arm_smlawt
- armintr/_arm_smlawb
- arm_neon/vdupq_lane_s8
- arm_neon/vaddl_s16
- arm_neon/vcombine_p16
- arm_neon/vzipq_u32
- arm_neon/poly16x8_t
- arm_neon/vshlq_n_s32
- arm_neon/vrshl_s8
- arm_neon/vst2_u64
- arm_neon/vrev64q_s8
- arm_neon/vst2q_lane_s32
- arm_neon/vld2_dup_s16
- arm_neon/vclt_u16
- arm_neon/vuzp_p8
- arm_neon/vshrq_n_s16
- arm_neon/vst3_u64
- arm_neon/vpmin_u16
- arm_neon/vld3q_lane_s32
- arm_neon/vmlal_s16
- arm_neon/poly16x4x4_t
- arm_neon/vorr_u16
- arm_neon/vsliq_n_s16
- arm_neon/vaddl_u8
- arm_neon/vld4_dup_s32
- arm_neon/vld2_f32
- arm_neon/vclt_u32
- arm_neon/vmull_lane_u16
- arm_neon/vsubw_u32
- arm_neon/vld2_dup_s32
- arm_neon/vuzp_s32
- arm_neon/vcge_s32
- arm_neon/vdup_lane_p16
- arm_neon/vpmin_s8
- arm_neon/vpaddlq_u32
- arm_neon/vmlaq_n_s32
- arm_neon/vshrn_n_u64
- arm_neon/vrshr_n_u16
- arm_neon/vld1_s64
- arm_neon/vbsl_u64
- armintr/_arm_smlad
- arm_neon/vqsub_s16
- arm_neon/vld4_p8
- arm_neon/vqdmulh_lane_s32
- arm_neon/vld3_dup_s64
- arm_neon/vornq_s32
- arm_neon/vpadd_u8
- arm_neon/vld3_lane_p16
- arm_neon/uint64x1x4_t
- arm_neon/vld3_u16
- armintr/_arm_shsax
- arm_neon/vabdq_u16
- arm_neon/vcgtq_f32
- arm_neon/vsubq_s8
- arm_neon/vget_low_f16
- arm_neon/vld4_dup_u64
- arm_neon/vst3_lane_s8
- armintr/_arm_ssat16
- arm_neon/vmlaq_f32
- arm_neon/vsri_n_s32
- arm_neon/vmax_u8
- arm_neon/vqadd_u8
- armintr/_arm_uqsub8
- armintr/_arm_clz
- arm_neon/vcgtq_s32
- arm_neon/vraddhn_s32
- arm_neon/vzip_s8
- arm_neon/veorq_s16
- arm_neon/vsetq_lane_s32
- arm_neon/vmul_n_u16
- armintr/_ReadBankedReg
- arm_neon/vld1q_u8
- arm_neon/vld4_p16
- arm_neon/int64x2x2_t
- arm_neon/vmaxq_s8
- arm_neon/vpmax_s16
- arm_neon/vshlq_u16
- arm_neon/vtrnq_p16
- arm_neon/vabal_u16
- arm_neon/vld2_lane_u16
- arm_neon/vrev32_u8
- arm_neon/vrshl_s32
- arm_neon/vget_low_f32
- arm_neon/vld2_s8
- arm_neon/vclzq_s16
- arm_neon/vqdmulhq_n_s16
- arm_neon/vset_lane_u64
- arm_neon/vld2_dup_p16
- arm_neon/vpaddlq_s32
- arm_neon/vld2q_p8
- arm_neon/vst3_lane_u8
- arm_neon/vld4_dup_f32
- arm_neon/vld2_s64
- arm_neon/vmls_u8
- arm_neon/vtbx4_u8
- arm_neon/vsetq_lane_f32
- arm_neon/vcvt_s32_f32
- arm_neon/vst3q_s32
- arm_neon/vmlsq_s8
- arm_neon/vmlaq_n_u16
- armintr/__iso_volatile_load64
- arm_neon/vcgt_u8
- arm_neon/vld2_dup_p8
- arm_neon/vmov_n_u8
- armintr/_arm_sasx
- arm_neon/vmovq_n_p16
- arm_neon/vmlaq_u32
- arm_neon/vst3_f32
- arm_neon/int32x2x4_t
- arm_neon/vld1q_lane_u64
- arm_neon/vclz_u16
- arm_neon/uint8x8_t
- arm_neon/vsub_u32
- arm_neon/vorn_u8
- armintr/__wfe
- arm_neon/vget_high_s16
- arm_neon/vzip_p8
- arm_neon/vmlal_lane_s16
- arm_neon/vmulq_u8
- armintr/_isunordered
- arm_neon/vld1_dup_f32
- arm_neon/vld4_lane_s16
- arm_neon/vdupq_n_s16
- arm_neon/vst3q_p16
- arm_neon/vst1_lane_f32
- arm_neon/float32x4x3_t
- arm_neon/vand_s8
- arm_neon/float32x2x4_t
- arm_neon/vld3_p8
- arm_neon/vmlaq_lane_u16
- armintr/_arm_uqsub16
- arm_neon/vget_high_s32
- arm_neon/vshl_n_s32
- arm_neon/vornq_s8
- arm_neon/vmlsl_n_u32
- arm_neon/vqshlq_n_s8
- arm_neon/int32x2x2_t
- arm_neon/int16x4x2_t
- arm_neon/vceqq_u8
- arm_neon/vcreate_f16
- arm_neon/vorn_s16
- arm_neon/vqmovn_s32
- arm_neon/vextq_u8
- arm_neon/vld4_s32
- armintr/_WriteStatusReg
- arm_neon/uint8x16_t
- arm_neon/vshrn_n_s64
- arm_neon/vmul_n_u32
- arm_neon/vabdl_u8
- arm_neon/vtbx3_s8
- arm_neon/vaddhn_s16
- arm_neon/vld3q_s8
- arm_neon/vmlsl_n_u16
- arm_neon/vrev64q_s32
- arm_neon/int16x8_t
- arm_neon/vext_s32
- arm_neon/vdupq_n_f32
- arm_neon/vld1q_lane_s32
- arm_neon/vqrshlq_u32
- arm_neon/vtbl2_u8
- arm_neon/vgetq_lane_u8
- arm_neon/veorq_u64
- arm_neon/vcntq_s8
- arm_neon/vbslq_p16
- arm_neon/vqnegq_s32
- arm_neon/vaddw_s32
- arm_neon/vmov_n_p8
- arm_neon/vmull_p8
- arm_neon/vld1_lane_u32
- arm_neon/vcombine_s16
- arm_neon/vqshrn_n_s64
- arm_neon/vceqq_s16
- arm_neon/vld4q_p16
- armintr/_ReadStatusReg
- armintr/_arm_qdadd
- arm_neon/uint32x4x2_t
- arm_neon/vcleq_u8
- armintr/_arm_sxtah
- arm_neon/vrhaddq_s32
- arm_neon/vset_lane_s64
- arm_neon/vld4_s64
- armintr/_DAddSatInt
- arm_neon/vorr_s8
- arm_neon/vst2_u32
- arm_neon/vshll_n_u16
- arm_neon/vld2_dup_u32
- arm_neon/vst3q_lane_s32
- arm_neon/vst3q_p8
- armintr/_MoveFromCoprocessor
- arm_neon/uint32x4_t
- arm_neon/vuzpq_s8
- arm_neon/vrecps_f32
- arm_neon/vst1_lane_s8
- arm_neon/vtbx1_s8
- arm_neon/uint16x8x3_t
- arm_neon/vpaddl_s16
- arm_neon/vsubq_s64
- arm_neon/vrsraq_n_u8
- arm_neon/vqadd_s64
- arm_neon/vst4_lane_s16
- arm_neon/vqadd_u16
- arm_neon/vset_lane_u32
- arm_neon/vand_u32
- arm_neon/vrsqrtsq_f32
- arm_neon/vqaddq_u32
- arm_neon/vsra_n_s64
- armintr/_arm_umlal
- arm_neon/vcvt_f32_f16
- arm_neon/vget_lane_u32
- arm_neon/vbsl_s8
- arm_neon/vrshlq_u32
- arm_neon/vqdmull_lane_s16
- arm_neon/vabsq_s32
- arm_neon/vld3_s8
- arm_neon/vst3q_lane_s16
- arm_neon/vld2q_lane_s16
- arm_neon/vst1_lane_s64
- arm_neon/vmov_n_u16
- arm_neon/vst4_lane_u8
- arm_neon/vshll_n_u32
- arm_neon/vqabs_s8
- arm_neon/vmvnq_u8
- arm_neon/vpadalq_u16
- arm_neon/vbsl_p16
- arm_neon/vqrshrn_n_u16
- arm_neon/vld3q_u32
- arm_neon/vcgeq_f32
- armintr/__iso_volatile_load32
- arm_neon/vrecpe_u32
- arm_neon/vld2_dup_u64
- arm_neon/vld3q_f32
- armintr/_arm_shsub8
- arm_neon/vdup_lane_s64
- arm_neon/vqrshl_s8
- arm_neon/vsliq_n_u16
- arm_neon/vld1q_u16
- arm_neon/vorr_u32
- arm_neon/vqrshl_s32
- armintr/__dmb
- arm_neon/veorq_s8
- arm_neon/vld1_u16
- arm_neon/vmov_n_u32
- arm_neon/vhsub_s16
- arm_neon/vst4q_lane_u16
- arm_neon/vbsl_u8
- armintr/_arm_uxtab
- arm_neon/vld2q_lane_f32
- arm_neon/vst2_p8
- armintr/_arm_smmla
- arm_neon/vaddw_u16
- arm_neon/vmlal_s8
- arm_neon/vtst_u32
- arm_neon/vtbl4_u8
- arm_neon/vcvt_n_f32_s32
- arm_neon/vcageq_f32
- arm_neon/vget_low_s16
- arm_neon/vdupq_n_u8
- arm_neon/vorn_s8
- arm_neon/uint8x16x3_t
- arm_neon/vabdq_u32
- arm_neon/vrev64_p8
- arm_neon/vqsubq_s8
- armintr/_arm_smlabb
- arm_neon/vbicq_s64
- arm_neon/vmaxq_u16
- arm_neon/vdup_n_u8
- arm_neon/veor_s8
- arm_neon/int16x8x2_t
- arm_neon/vcvtq_s32_f32
- arm_neon/vtrn_u16
- arm_neon/vbslq_s32
- arm_neon/vld1q_dup_u32
- arm_neon/vmul_n_f32
- arm_neon/vqrshl_u32
- arm_neon/vqsubq_s16
- arm_neon/vst2_lane_f16
- armintr/_arm_smulwt
- arm_neon/vrshrn_n_u32
- arm_neon/vget_high_p16
- arm_neon/vqadd_u64
- arm_neon/vsli_n_s32
- arm_neon/vhadd_u32
- arm_neon/vmlsl_lane_u16
- arm_neon/vclzq_u32
- arm_neon/vqshrun_n_s64
- arm_neon/vrev64q_u32
- arm_neon/vqshrun_n_s16
- arm_neon/vrev32q_s8
- armintr/_arm_shasx
- arm_neon/vaddl_s8
- armintr/_arm_smull
- arm_neon/vabaq_u8
- armintr/_arm_revsh
- arm_neon/vsubq_f32
- arm_neon/poly16x4x2_t
- arm_neon/poly8x8x3_t
- arm_neon/vsubhn_s64
- arm_neon/vcle_u16
- arm_neon/poly8x16x3_t
- arm_neon/vqdmlsl_n_s16
- arm_neon/vqshl_u64
- arm_neon/vcge_u16
- armintr/_arm_uasx
- arm_neon/vmovl_s32
- arm_neon/vst1q_lane_u16
- arm_neon/vbic_u32
- arm_neon/vld2_s16
- armintr/_arm_qasx
- arm_neon/vorrq_u8
- arm_neon/vst2_s32
- armintr/_WriteBankedReg
- arm_neon/veorq_s64
- arm_neon/vld4_lane_f32
- arm_neon/vcreate_u8
- arm_neon/vset_lane_u8
- arm_neon/vandq_u16
- arm_neon/vrsubhn_s64
- arm_neon/vst1q_lane_p16
- arm_neon/uint8x8x2_t
- arm_neon/vmlsl_s8
- arm_neon/vmax_s32
- arm_neon/uint32x4x3_t
- arm_neon/vld4_dup_u16
- arm_neon/vabs_s32
- arm_neon/vld3_dup_u32
- arm_neon/vrshl_u16
- arm_neon/vcle_u8
- arm_neon/vqshl_n_u16
- arm_neon/vbic_s8
- arm_neon/float32x4x2_t
- arm_neon/vmls_f32
- arm_neon/vshll_n_u8
- arm_neon/vminq_s8
- arm_neon/vmlsq_lane_f32
- arm_neon/vst1q_f16
- arm_neon/vst1_lane_u64
- arm_neon/vrhadd_u8
- arm_neon/vclt_s32
- arm_neon/vst2_p16
- arm_neon/vrshrq_n_u16
- arm_neon/vneg_s32
- arm_neon/vmovl_s16
- arm_neon/vqshlq_s8
- arm_neon/vld1_s8
- arm_neon/vqdmulh_s32
- arm_neon/vcls_s8
- armintr/__trap
- arm_neon/vuzp_u32
- armintr/_CopyInt64FromDouble
- arm_neon/int8x16x2_t
- arm_neon/vmovn_s32
- arm_neon/vget_high_s8
- arm_neon/veor_s64
- armintr/_arm_uadd8
- arm_neon/vrev16_u8
- arm_neon/vbicq_u64
- arm_neon/vst4_lane_f16
- arm_neon/vst3_s32
- arm_neon/poly8x8_t
- arm_neon/vtstq_u16
- arm_neon/vld1_lane_s8
- arm_neon/float32x4x4_t
- arm_neon/vst2_s16
- arm_neon/vqrdmulhq_s32
- arm_neon/vqdmulhq_s16
- arm_neon/vrshrq_n_s8
- arm_neon/vcle_s32
- arm_neon/vtbl3_p8
- arm_neon/vbslq_u8
- arm_neon/vst4_u64
- armintr/_arm_umaal
- arm_neon/vshll_n_s8
- arm_neon/vcvt_u32_f32
- arm_neon/vld4q_p8
- arm_neon/vsetq_lane_u16
- arm_neon/vabd_u8
- arm_neon/vclz_u8
- arm_neon/vsubq_u32
- arm_neon/vld1q_lane_p16
- arm_neon/vcgtq_s16
- arm_neon/vmla_lane_s32
- arm_neon/vshlq_n_s64
- arm_neon/vbsl_u32
- arm_neon/vqshlq_s16
- armintr/_arm_qadd8
- arm_neon/vrshr_n_s32
- armintr/_CountOneBits64
- arm_neon/vceq_u32
- arm_neon/vbsl_p8
- arm_neon/uint16x8x2_t
- arm_neon/vsli_n_s16
- arm_neon/vmla_n_s32
- arm_neon/vld4_dup_u32
- arm_neon/vshrq_n_s8
- arm_neon/vqaddq_s8
- arm_neon/vshl_n_u64
- arm_neon/vtbl2_p8
- arm_neon/vcleq_u32
- arm_neon/vqsub_u32
- arm_neon/vmovl_u8
- arm_neon/vmlal_u8
- arm_neon/vmul_s8
- armintr/_MoveFromCoprocessor64
- arm_neon/vrsraq_n_s16
- arm_neon/vdupq_n_u32
- arm_neon/vmov_n_s16
- arm_neon/vst4_lane_p8
- arm_neon/vld1_s32
- arm_neon/vst4_p8
- arm_neon/vsriq_n_u32
- arm_neon/vqdmull_n_s16
- arm_neon/vshlq_u32
- arm_neon/vld3_u8
- armintr/_arm_usub16
- arm_neon/vmlsq_lane_s16
- arm_neon/vmovq_n_s8
- arm_neon/int32x4x2_t
- arm_neon/vld4q_u8
- arm_neon/poly16x8x2_t
- arm_neon/vld1q_u64
- arm_neon/vld3q_lane_s16
- arm_neon/int64x1x2_t
- arm_neon/vshlq_n_s8
- arm_neon/vrshl_s64
- arm_neon/vqshl_n_u8
- armintr/_arm_qadd
- armintr/_DSubSatInt
- armintr/_arm_usat16
- arm_neon/vmull_s8
- arm_neon/vsub_s8
- arm_neon/vmovq_n_u16
- arm_neon/vst4_u16
- arm_neon/vmlsl_lane_u32
- arm_neon/vsliq_n_p16
- arm_neon/vmovn_u32
- arm_neon/vbic_u16
- arm_neon/vtbx2_p8
- arm_neon/vrsubhn_s32
- armintr/_SubSatInt
- arm_neon/vst3_u8
- arm_neon/vdupq_n_s32
- arm_neon/vcntq_p8
- arm_neon/vst4_f32
- arm_neon/vbic_s64
- arm_neon/vld3_s64
- arm_neon/vrsra_n_s64
- arm_neon/vqabsq_s16
- arm_neon/vsriq_n_p8
- arm_neon/vst2_lane_p16
- arm_neon/vabsq_s16
- arm_neon/vcombine_u8
- arm_neon/vld2q_p16
- armintr/_CountOneBits
- armintr/__prefetch
- arm_neon/vld3_dup_u64
- arm_neon/vld2q_s16
- arm_neon/vget_low_p16
- arm_neon/vuzpq_u8
- arm_neon/vrev32q_s16
- armintr/_AddSatInt
- arm_neon/uint16x4x2_t
- arm_neon/vmov_n_s32
- arm_neon/vaddl_u16
- arm_neon/vqaddq_s64
- arm_neon/vmlaq_u16
- arm_neon/vsli_n_s8
- armintr/_arm_sxth
- arm_neon/vorr_s32
- arm_neon/vsra_n_u64
- arm_neon/vst2_f16
- arm_neon/vcombine_u16
- arm_neon/vabs_s16
- arm_neon/vsubhn_s32
- arm_neon/vst1q_lane_u32
- arm_neon/vst3_p8
- arm_neon/vqshrun_n_s32
- arm_neon/vcreate_s64
- arm_neon/vld4q_lane_s16
- arm_neon/vzipq_u16
- arm_neon/vmin_s32
- armintr/_CopyInt32FromFloat
- arm_neon/vcgtq_u32
- arm_neon/vabdl_s32
- arm_neon/vqshlq_n_u16
- arm_neon/int8x16x4_t
- arm_neon/vqrdmulh_n_s32
- arm_neon/vqaddq_u64
- arm_neon/vhaddq_s8
- arm_neon/vshll_n_s16
- arm_neon/vuzp_u8
- arm_neon/vaddl_u32
- arm_neon/vld4q_s16
- arm_neon/vqmovun_s16
- arm_neon/vld1q_lane_s8
- arm_neon/vld2_lane_u32
- arm_neon/vrshr_n_s8
- arm_neon/vmlaq_s16
- armintr/_CopyFloatFromInt32
- arm_neon/vmul_f32
- arm_neon/vmlaq_n_f32
- arm_neon/vst4_s16
- arm_neon/vld1_dup_s32
- arm_neon/vmul_u16
- arm_neon/vhaddq_s16
- arm_neon/vst1q_lane_f32
- arm_neon/vrhaddq_u16
- arm_neon/vbicq_u32
- arm_neon/vrev32_s8
- arm_neon/vmlaq_s8
- arm_neon/vmin_s16
- arm_neon/vst3_lane_p16
- arm_neon/vst2q_lane_f32
- arm_neon/vld4q_lane_f32
- arm_neon/vget_low_u16
- arm_neon/vqsub_s32
- arm_neon/vtbl1_s8
- arm_neon/vmovn_s64
- arm_neon/vpmax_s8
- arm_neon/int8x16_t
- arm_neon/vpmin_u8
- arm_neon/vdup_lane_p8
- arm_neon/vsetq_lane_u64
- arm_neon/vuzpq_u16
- arm_neon/vcgeq_u16
- arm_neon/uint8x16x2_t
- armintr/_arm_rev16
- armintr/_arm_sxtb
- arm_neon/vsliq_n_u64
- arm_neon/vmovq_n_u8
- arm_neon/vshlq_n_u32
- arm_neon/vcombine_s64
- armintr/_arm_qsax
- arm_neon/vmin_f32
- armintr/_arm_sadd16
- arm_neon/vmlsq_n_s16
- arm_neon/vorr_u64
- arm_neon/vqrshrun_n_s64
- arm_neon/vld2q_lane_s32
- arm_neon/vgetq_lane_p16
- arm_neon/vrev32_s16
- arm_neon/vqshl_u16
- arm_neon/vtrn_s8
- arm_neon/vst1q_lane_s64
- arm_neon/vtbl4_p8
- arm_neon/vst1_p16
- arm_neon/vmvn_u8
- arm_neon/vld2_lane_u8
- arm_neon/vld2q_u16
- arm_neon/vmovl_s8
- arm_neon/vbslq_u64
- arm_neon/vmls_s8
- arm_neon/vld3q_p16
- arm_neon/vtbl3_u8
- arm_neon/vabs_f32
- arm_neon/vsraq_n_s8
- arm_neon/vqadd_s32
- arm_neon/vmulq_n_s16
- arm_neon/vst3q_s8
- arm_neon/vaddhn_s64
- arm_neon/vmul_n_s16
- arm_neon/vtbl1_p8
- arm_neon/uint64x2x3_t
- arm_neon/vmlsq_s32
- arm_neon/vld2q_lane_u32
- arm_neon/vaddq_u8
- arm_neon/vcombine_f16
- arm_neon/vandq_s16
- arm_neon/vst4q_lane_p16
- arm_neon/vsri_n_u8
- arm_neon/vst3_lane_p8
- arm_neon/vst3_lane_s16
- arm_neon/vdup_n_s16
- arm_neon/vbicq_s8
- arm_neon/vdup_lane_u8
- arm_neon/vst4q_lane_s32
- arm_neon/vqrshl_u16
- arm_neon/vrsra_n_u32
- arm_neon/vdupq_lane_p8
- arm_neon/vld3_lane_u8
- arm_neon/vqrdmulh_n_s16
- arm_neon/vpmin_s32
- armintr/__cps
- arm_neon/vshl_u32
- armintr/_arm_uadd16
- arm_neon/vld3_s16
- arm_neon/vcvt_f32_s32
- arm_neon/vshlq_n_u64
- arm_neon/vrev64q_u8
- arm_neon/vextq_u16
- arm_neon/vsubl_s16
- arm_neon/vget_lane_p8
- arm_neon/vabal_s16
- arm_neon/vrecpeq_u32
- arm_neon/vminq_u8
- arm_neon/veor_s16
- arm_neon/vmull_n_u16
- arm_neon/vshl_n_u8
- arm_neon/vrev32q_u8
- arm_neon/vandq_s8
- arm_neon/vrshlq_s16
- arm_neon/vst4q_p16
- arm_neon/vandq_s32
- armintr/_MoveToCoprocessor2
- arm_neon/vqdmlsl_lane_s32
- arm_neon/vld1q_s64
- arm_neon/vmull_n_s16
- arm_neon/vneg_s16
- arm_neon/vqshluq_n_s64
- arm_neon/vst2_lane_s32
- arm_neon/vmvnq_u16
- arm_neon/vshll_n_s32
- arm_neon/vld3_dup_s8
- arm_neon/vtstq_s32
- arm_neon/vmlsl_u32
- arm_neon/vqdmulhq_lane_s16
- arm_neon/vaddl_s32
- armintr/_CountLeadingZeros
- arm_neon/vqrshrn_n_s16
- arm_neon/vmla_lane_u32
- arm_neon/vst1_u8
- arm_neon/vshl_u64
- arm_neon/vshr_n_u8
- arm_neon/vmull_lane_s32
- arm_neon/vmlal_lane_u32
- arm_neon/vsubl_s8
- arm_neon/float32x2x2_t
- armintr/_arm_bfc
- arm_neon/vaddq_s16
- arm_neon/vmlal_lane_s32
- arm_neon/vpadd_u16
- arm_neon/vst2q_lane_u16
- arm_neon/vld4_s8
- arm_neon/vst1q_s8
- arm_neon/vshrq_n_u64
- arm_neon/vsli_n_u16
- arm_neon/vqrdmulh_lane_s32
- arm_neon/vst4_lane_u16
- arm_neon/vabdq_f32
- arm_neon/vld2_lane_f16
- arm_neon/vqsub_u64
- arm_neon/vsub_f32
- arm_neon/vld1q_s16
- arm_neon/vmaxq_s16
- arm_neon/vcombine_u32
- arm_neon/vrsraq_n_u32
- armintr/_arm_smusdx
- arm_neon/vrev16_s8
- arm_neon/vqdmulh_n_s32
- arm_neon/vmul_s32
- arm_neon/vabdq_s32
- arm_neon/veor_u64
- arm_neon/vmlsl_n_s32
- arm_neon/vsub_s16
- arm_neon/vadd_u16
- arm_neon/vsriq_n_u16
- arm_neon/vmla_u32
- arm_neon/vuzpq_s32
- arm_neon/vst4q_s8
- arm_neon/vaddhn_u32
- arm_neon/vmlaq_lane_f32
- arm_neon/vld3_lane_s8
- arm_neon/vsliq_n_u32
- arm_neon/vqrshlq_s8
- arm_neon/vqdmlal_n_s32
- arm_neon/uint8x16x4_t
- arm_neon/vcgtq_u16
- arm_neon/vandq_u32
- arm_neon/vld4q_lane_u32
- arm_neon/vzip_p16
- arm_neon/vget_low_p8
- armintr/_arm_shadd8
- arm_neon/vmovn_s16
- arm_neon/vcge_u8
- arm_neon/vld2q_f32
- arm_neon/vaba_u32
- armintr/__iso_volatile_store8
- arm_neon/vst2q_p16
- arm_neon/vmul_s16
- arm_neon/vand_s16
- arm_neon/vtbx4_p8
- arm_neon/vceq_u8
- arm_neon/vrhaddq_s16
- arm_neon/vgetq_lane_f32
- arm_neon/vqshl_s8
- arm_neon/vbslq_f32
- arm_neon/vrsqrts_f32
- arm_neon/vld2q_s8
- arm_neon/vtbl1_u8
- arm_neon/vtst_u8
- arm_neon/vrev64q_f32
- arm_neon/vcle_s8
- arm_neon/vsetq_lane_p16
- arm_neon/vcreate_p16
- arm_neon/vabal_s32
- armintr/_arm_smlald
- arm_neon/vmla_f32
- arm_neon/vtbx2_s8
- arm_neon/int64x1x3_t
- arm_neon/vclz_s8
- arm_neon/vorr_s16
- arm_neon/vornq_s64
- arm_neon/vst1q_u64
- arm_neon/vdupq_n_s8
- armintr/_arm_sadd8
- arm_neon/vextq_s32
- armintr/_arm_smuadx
- armintr/_arm_qsub
- arm_neon/vadd_f32
- arm_neon/vrshrq_n_s16
- arm_neon/vqsub_s8
- arm_neon/vld3_f32
- arm_neon/vhadd_s8
- arm_neon/vmull_n_u32
- arm_neon/vdup_n_u64
- arm_neon/vsubw_s32
- armintr/_arm_sxtab
- armintr/_arm_uxtb16
- arm_neon/vmvn_s16
- arm_neon/vst1_lane_s16
- arm_neon/vqrdmulhq_n_s32
- arm_neon/vsriq_n_s32
- arm_neon/poly8x16x2_t
- arm_neon/vadd_u8
- arm_neon/vuzpq_p8
- arm_neon/vst2q_p8
- armintr/__wfi
- arm_neon/vget_high_u16
- arm_neon/vqrshl_u64
- arm_neon/vld1_dup_s64
- arm_neon/vqrshrn_n_s32
- arm_neon/vrshr_n_s64
- arm_neon/vst3_s8
- arm_neon/poly16x4x3_t
- arm_neon/vqrdmulh_lane_s16
- arm_neon/vmvnq_u32
- arm_neon/vqsubq_u32
- arm_neon/vmovq_n_p8
- arm_neon/vtrn_s16
- arm_neon/vld2q_u32
- arm_neon/vqsubq_u16
- arm_neon/vrsqrteq_u32
- arm_neon/vadd_u64
- armintr/_arm_usat
- arm_neon/vcvtq_n_u32_f32
- arm_neon/vaddq_s8
- arm_neon/vrsraq_n_u16
- arm_neon/vqabs_s16
- arm_neon/vsra_n_s8
- arm_neon/vsra_n_s16
- arm_neon/vqshlq_n_u8
- arm_neon/vpadal_s8
- arm_neon/vmlal_n_u16
- armintr/_CopyDoubleFromInt64
- arm_neon/vaddw_u8
- arm_neon/vmulq_n_s32
- arm_neon/vqaddq_s32
- arm_neon/vmla_lane_f32
- arm_neon/vmlaq_lane_s32
- arm_neon/vld1q_dup_u64
- arm_neon/uint16x8_t
- arm_neon/vld2_s32
- arm_neon/vcltq_f32
- arm_neon/vst4q_f32
- arm_neon/vsri_n_u16
- arm_neon/vshlq_s32
- arm_neon/vgetq_lane_u32
- arm_neon/vld1q_dup_f16
- arm_neon/vrev64q_s16
- arm_neon/vrshrq_n_u32
- arm_neon/vld2q_s32
- arm_neon/vcgtq_s8
- arm_neon/vsubhn_u64
- arm_neon/vmls_n_s32
- armintr/_arm_smmlar
- arm_neon/vld3_dup_u8
- arm_neon/vld3q_lane_p16
- arm_neon/vld2_dup_s64
- arm_neon/vqabs_s32
- arm_neon/vqaddq_u8
- arm_neon/vminq_u32
- arm_neon/vpaddl_u16
- arm_neon/vaba_s16
- arm_neon/vmul_u32
- arm_neon/vst1_lane_u16
- arm_neon/vcreate_f32
- arm_neon/vcvt_f16_f32
- arm_neon/vset_lane_s32
- arm_neon/vshl_s8
- arm_neon/vcgt_s16
- arm_neon/vtrn_f32
- arm_neon/vget_high_s64
- arm_neon/vld3_dup_p8
- arm_neon/vcreate_u64
- arm_neon/vext_u64
- arm_neon/vld1q_dup_s16
- arm_neon/vget_lane_s16
- arm_neon/vqdmlal_s16
- arm_neon/vld2_p16
- arm_neon/vld4_u16
- armintr/_arm_smlalbb
- arm_neon/vrev64_u8
- arm_neon/vbslq_s64
- arm_neon/vsubw_u16
- arm_neon/vrsubhn_u32
- arm_neon/vabdq_u8
- arm_neon/vmls_n_u32
- arm_neon/vshr_n_s32
- arm_neon/vmulq_n_u32
- arm_neon/vst3_p16
- arm_neon/vrev32_u16
- arm_neon/int8x8x3_t
- arm_neon/vst2q_lane_u32
- arm_neon/vextq_p16
- arm_neon/vtrnq_f32
- armintr/_arm_smultt
- arm_neon/vqneg_s8
- arm_neon/vmlsq_lane_s32
- arm_neon/vmov_n_p16
- arm_neon/vraddhn_u64
- arm_neon/vrhadd_u32
- arm_neon/vrev64_u32
- arm_neon/vrshrn_n_s32
- arm_neon/vld4q_f32
- arm_neon/vst2_s8
- arm_neon/vrsqrteq_f32
- arm_neon/uint16x4_t
- arm_neon/vget_low_s8
- arm_neon/vst2_lane_u32
- arm_neon/vhsub_s32
- arm_neon/vqdmull_lane_s32
- armintr/_arm_smulwb
- arm_neon/vmlsl_u8
- arm_neon/vdup_lane_s16
- arm_neon/vtbx4_s8
- arm_neon/vld4q_lane_u16
- arm_neon/vget_high_u8
- arm_neon/vclzq_s32
- arm_neon/vld1q_dup_f32
- arm_neon/vtrn_u8
- arm_neon/vqabsq_s8
- arm_neon/vdup_lane_f32
- arm_neon/vqrdmulh_s16
- arm_neon/vst4_u32
- arm_neon/vdup_lane_u32
- arm_neon/vst4_u8
- arm_neon/vmovq_n_s32
- arm_neon/vld2_lane_s8
- arm_neon/vld3_u32
- arm_neon/vsubl_u16
- arm_neon/vqshlu_n_s8
- arm_neon/float32x4_t
- arm_neon/vqshl_n_s32
- arm_neon/float32x2x3_t
- armintr/__hvc
- arm_neon/vst1q_lane_f16
- arm_neon/vmvnq_s16
- arm_neon/vst3q_lane_f32
- arm_neon/vld1q_dup_u8
- arm_neon/vmlsq_s16
- arm_neon/vget_lane_u8
- arm_neon/vld1_lane_s32
- arm_neon/vst4q_s16
- armintr/_arm_qsub8
- arm_neon/vorrq_s32
- arm_neon/vsriq_n_s8
- arm_neon/vqshrn_n_u64
- arm_neon/vdup_n_s32
- armintr/_arm_uhsub8
- arm_neon/vld3_lane_s32
- arm_neon/vbsl_s64
- arm_neon/vld1_dup_f16
- arm_neon/vsli_n_u64
- arm_neon/vraddhn_u32
- arm_neon/vsub_u16
- arm_neon/vcltq_u32
- arm_neon/vminq_f32
- arm_neon/vshl_n_s64
- arm_neon/vld4_u32
- arm_neon/vld1_u32
- arm_neon/vaddhn_u16
- arm_neon/vcvtq_n_f32_s32
- arm_neon/vorn_u64
- arm_neon/vsubhn_u16
- arm_neon/int64x1_t
- arm_neon/vst1q_lane_s8
- arm_neon/vld1q_dup_s32
- arm_neon/vrev32_p8
- arm_neon/vst3q_lane_p16
- arm_neon/vrecpeq_f32
- arm_neon/int8x8x4_t
- arm_neon/vshr_n_u32
- arm_neon/vdupq_lane_s64
- arm_neon/vpaddlq_s8
- arm_neon/vqshl_n_u32
- arm_neon/vmul_u8
- arm_neon/vtbx2_u8
- arm_neon/vshr_n_u64
- arm_neon/vqrshlq_s16
- arm_neon/vst3_lane_u16
- arm_neon/vqsub_u8
- arm_neon/vrsra_n_s16
- arm_neon/vaba_s32
- arm_neon/vsri_n_u64
- arm_neon/vst3q_lane_u32
- arm_neon/vmlsq_n_u32
- arm_neon/poly8x16_t
- arm_neon/vld2_u8
- armintr/_arm_smmulr
- arm_neon/vtst_s16
- armintr/_arm_smmls
- arm_neon/vqdmulh_s16
- arm_neon/vtrnq_u8
- arm_neon/vset_lane_p8
- arm_neon/vmlsl_u16
- arm_neon/vshrn_n_u16
- arm_neon/vld1_dup_p8
- arm_neon/vrev16q_s8
- arm_neon/vmov_n_s8
- arm_neon/vld1_u64
- arm_neon/vpmin_f32
- arm_neon/vmla_n_u16
- arm_neon/vst1_f16
- arm_neon/vqdmlsl_s16
- arm_neon/vmin_u32
- armintr/_arm_qsub16
- arm_neon/vcage_f32
- arm_neon/vornq_u32
- arm_neon/vpadd_s16
- arm_neon/vld1_u8
- arm_neon/vhsubq_s16
- arm_neon/vld1_dup_u32
- arm_neon/vld4_u64
- armintr/_MulHigh
- arm_neon/vmaxq_u8
- arm_neon/vget_lane_u16
- arm_neon/vld2q_u8
- arm_neon/vld1q_dup_p16
- arm_neon/vsraq_n_u8
- arm_neon/vqdmlsl_n_s32
- arm_neon/vst1_s16
- arm_neon/vst1q_s32
- arm_neon/vmaxq_f32
- arm_neon/vqdmulh_lane_s16
- armintr/__isb
- arm_neon/vuzpq_p16
- arm_neon/vmls_lane_s16
- arm_neon/vtbl4_s8
- arm_neon/vst1_lane_p8
- arm_neon/vsubw_s8
- arm_neon/vmin_u8
- arm_neon/vzip_u16
- arm_neon/vld4q_u16
- arm_neon/vshrn_n_s32
- arm_neon/vpadal_u16
- arm_neon/vorrq_s8
- arm_neon/vrshlq_u64
- arm_neon/vst3_lane_s32
- arm_neon/vqshluq_n_s32
- armintr/_arm_shsub16
- arm_neon/vst1_u32
- arm_neon/vrhadd_s16
- arm_neon/vzipq_s32
- arm_neon/vshrq_n_u16
- arm_neon/vcls_s32
- arm_neon/vceq_s8
- arm_neon/vld2q_lane_f16
- arm_neon/vst4q_u8
- arm_neon/vraddhn_u16
- arm_neon/vget_lane_u64
- armintr/_arm_smlsld
- arm_neon/vld3_u64
- arm_neon/vld1_lane_s16
- arm_neon/vabd_f32
- arm_neon/vdupq_n_u16
- armintr/__iso_volatile_store64
- arm_neon/vqsubq_u8
- arm_neon/poly16x8x3_t
- arm_neon/vcltq_s32
- arm_neon/vqnegq_s16
- arm_neon/vqsub_u16
- arm_neon/vaddq_s32
- arm_neon/vqshl_n_s64
- arm_neon/vabdl_s8
- arm_neon/vclsq_s16
- arm_neon/vpaddl_u8
- arm_neon/vmlsq_n_u16
- armintr/_arm_uqadd8
- arm_neon/vhsub_u32
- arm_neon/vset_lane_s16
- arm_neon/vsubl_u32
- arm_neon/vld3_lane_f32
- arm_neon/vcle_s16
- arm_neon/vmovl_u32
- arm_neon/vst3_lane_f16
- arm_neon/vcaltq_f32
- arm_neon/vsubq_s32
- arm_neon/vand_s64
- arm_neon/vst2_u8
- arm_neon/vcombine_p8
- arm_neon/vqdmlal_s32
- arm_neon/vsub_s32
- armintr/_arm_uxtab16
- arm_neon/vmlsq_n_f32
- armintr/_arm_qdsub
- arm_neon/vhaddq_u32
- arm_neon/vhsubq_u16
- arm_neon/vmlsq_lane_u16
- arm_neon/vst4_s64
- armintr/_CountLeadingOnes
- armintr/_arm_smlabt
- arm_neon/vcombine_s32
- arm_neon/vld4_lane_f16
- arm_neon/vadd_s64
- arm_neon/vorrq_u32
- armintr/__sev
- arm_neon/vdupq_lane_s32
- arm_neon/vrecpsq_f32
- arm_neon/vbicq_u16
- arm_neon/vld1_lane_p16
- arm_neon/vrshr_n_u32
- arm_neon/vcgeq_s32
- arm_neon/vld4_dup_s16
- arm_neon/vld1q_p8
- arm_neon/vrshlq_u16
- arm_neon/vmlaq_lane_u32
- arm_neon/vsub_s64
- arm_neon/vcreate_u16
- arm_neon/vget_lane_s32
- arm_neon/vuzp_f32
- arm_neon/vld2_lane_p8
- arm_neon/vuzp_u16
- arm_neon/vorrq_s16
- armintr/_arm_smlaltb
- arm_neon/vrshrn_n_s16
- arm_neon/vabd_s8
- arm_neon/vnegq_s8
- arm_neon/vst4q_u16
- arm_neon/vst1q_lane_s32
- arm_neon/vst1_lane_s32
- arm_neon/vmla_u16
- arm_neon/vmls_lane_s32
- arm_neon/vtst_s8
- arm_neon/vcgeq_s8
- arm_neon/poly8x8x4_t
- arm_neon/vqsub_s64
- armintr/_arm_uqasx
- arm_neon/vld1_lane_u64
- arm_neon/vminq_s16
- arm_neon/vmulq_u32
- arm_neon/vqrshlq_u8
- arm_neon/vdupq_n_p16
- arm_neon/vld4_dup_f16
- arm_neon/vcls_s16
- arm_neon/vmov_n_u64
- arm_neon/vmla_s32
- arm_neon/vrshl_s16
- arm_neon/vcalt_f32
- arm_neon/int64x2x3_t
- arm_neon/vsub_u8
- arm_neon/vzipq_u8
- arm_neon/vrshrn_n_u64
- arm_neon/vrshlq_s32
- arm_neon/vorr_s64
- arm_neon/vqrshl_s16
- arm_neon/vceqq_u16
- arm_neon/vmulq_n_u16
- arm_neon/vmlaq_u8
- arm_neon/vsri_n_s64
- arm_neon/vld3q_u8
- arm_neon/vld1_dup_s16
- arm_neon/vld1q_s32
- arm_neon/vsri_n_s16
- arm_neon/vshlq_u8
- arm_neon/vsli_n_s64
- arm_neon/vmull_lane_u32
- arm_neon/vshl_s64
- arm_neon/vcreate_s16
- arm_neon/uint8x8x4_t
- arm_neon/vqshrn_n_s32
- arm_neon/vqshlq_u32
- arm_neon/vmlal_n_u32
- arm_neon/vtrnq_s16
- arm_neon/vshr_n_s64
- arm_neon/vst2_u16
- arm_neon/vtrn_s32
- arm_neon/vsubhn_u32
- arm_neon/vbicq_s16
- arm_neon/vsetq_lane_s8
- arm_neon/vrsubhn_s16
- arm_neon/vhsub_u8
- arm_neon/vcleq_s32
- arm_neon/vld4_dup_s8
- arm_neon/vmull_u32
- arm_neon/vrshr_n_s16
- arm_neon/vst1q_lane_s16
- arm_neon/vmlsq_lane_u32
- arm_neon/vnegq_f32
- arm_neon/vmin_s8
- arm_neon/vrev16_p8
- arm_neon/vbic_u8
- arm_neon/vclzq_u16
- arm_neon/vcge_u32
- arm_neon/vget_high_u64
- arm_neon/vabsq_s8
- arm_neon/vhaddq_u16
- arm_neon/vsraq_n_s64
- arm_neon/vld2_u32
- arm_neon/vld2_lane_f32
- arm_neon/vqrshrn_n_u32
- arm_neon/vbslq_s8
- armintr/_CountLeadingZeros64
- arm_neon/vbicq_u8
- arm_neon/vdup_lane_s8
- arm_neon/vpadd_s32
- arm_neon/vld3q_lane_f16
- arm_neon/vaba_u8
- arm_neon/vqshlq_u16
- arm_neon/vst1q_u8
- arm_neon/vst4q_lane_f16
- arm_neon/vshl_n_u16
- armintr/_arm_smladx
- arm_neon/vmla_lane_s16
- arm_neon/vornq_u8
- arm_neon/vqneg_s32
- arm_neon/vadd_s8
- arm_neon/vcle_u32
- arm_neon/vclzq_u8
- arm_neon/vtbx1_u8
- armintr/_CountLeadingOnes64
- armintr/__dsb
- arm_neon/vaddq_u32
- arm_neon/vclsq_s8
- arm_neon/vdup_n_s64
- arm_neon/vmax_s16
- arm_neon/vst2q_u32
- arm_neon/vsetq_lane_s64
- arm_neon/vtst_p8
- arm_neon/vabs_s8
- arm_neon/vqshl_n_s16
- arm_neon/vqrshrn_n_u64
- arm_neon/vaddw_s8
- armintr/_arm_uhadd16
- arm_neon/vsriq_n_p16
- arm_neon/vld4_lane_u32
- arm_neon/vneg_f32
- armintr/_MoveToCoprocessor
- arm_neon/vmvnq_s8
- arm_neon/vld1q_lane_p8
- arm_neon/uint32x2x3_t
- arm_neon/vrshrn_n_u16
- arm_neon/vld3_f16
- arm_neon/vsriq_n_s16
- arm_neon/vshlq_n_s16
- arm_neon/vabal_u8
- arm_neon/vqshluq_n_s16
- arm_neon/vst2_lane_u16
- arm_neon/vbic_s16
- arm_neon/vqshl_n_u64
- arm_neon/vcagt_f32
- arm_neon/vpadalq_s8
- arm_neon/vclz_s32
- arm_neon/vld1_lane_s64
- arm_neon/vget_high_p8
- arm_neon/uint64x1_t
- arm_neon/vextq_s16
- arm_neon/vpadd_s8
- arm_neon/vrsubhn_u64
- arm_neon/vst3q_f16
- arm_neon/vdupq_lane_u16
- arm_neon/vrshrq_n_u64
- arm_neon/vmovq_n_f32
- arm_neon/vld1q_dup_u16
- arm_neon/vshr_n_u16
- arm_neon/uint32x2_t
- armintr/_arm_umull
- arm_neon/vtrnq_u16
- arm_neon/vsetq_lane_u32
- arm_neon/vneg_s8
- arm_neon/vsetq_lane_u8
- arm_neon/vst2q_lane_s16
- arm_neon/vqmovun_s32
- armintr/_arm_usad8
- armintr/_arm_pkhbt
- arm_neon/uint16x4x3_t
- arm_neon/vsra_n_s32
- arm_neon/vqmovun_s64
- arm_neon/vld1q_dup_s8
- arm_neon/vaddhn_s32
- arm_neon/vpmax_f32
- arm_neon/vpadd_u32
- arm_neon/vhsubq_u32
- arm_neon/vqrshrun_n_s32
- arm_neon/vadd_s32
- arm_neon/vclt_s8
- arm_neon/vorrq_s64
- arm_neon/vst4q_f16
- arm_neon/vst1_s32
- arm_neon/vceq_p8
- arm_neon/vsubw_s16
- arm_neon/vgetq_lane_u64
- arm_neon/vmla_n_u32
- arm_neon/vcvtq_f32_s32
- arm_neon/vld1q_u32
- arm_neon/vmax_f32
- armintr/_isunorderedf
- arm_neon/vrshl_u8
- arm_neon/vld4_dup_s64
- arm_neon/vqaddq_u16
- arm_neon/vld4q_lane_f16
- arm_neon/vceqq_p8
- arm_neon/vsubw_u8
- arm_neon/vqmovn_u16
- armintr/_arm_smlsldx
- arm_neon/vcreate_p8
- arm_neon/vqdmull_n_s32
- arm_neon/uint64x2_t
- arm_neon/vmls_s32
- arm_neon/vst3q_f32
- armintr/_arm_bfi
- armintr/_arm_qadd16
- arm_neon/vrshlq_s8
- arm_neon/vget_lane_p16
- arm_neon/vld2_p8
- arm_neon/vld3_lane_u32
- armintr/_MoveFromCoprocessor2
- arm_neon/vqshl_u8
- arm_neon/poly8_t
- arm_neon/vhadd_u16
- arm_neon/vmla_lane_u16
- arm_neon/vshrq_n_u8
- arm_neon/vuzpq_f32
- arm_neon/vmls_lane_f32
- arm_neon/vqneg_s16
- arm_neon/vtrn_p16
- arm_neon/vshrn_n_u32
- arm_neon/vaddhn_u64
- arm_neon/vabal_u32
- arm_neon/vld1q_lane_u32
- arm_neon/vrsraq_n_s32
- arm_neon/vandq_u64
- arm_neon/vqdmull_s32
- arm_neon/vext_s16
- arm_neon/vaddw_s16
- arm_neon/vrev64q_p8
- arm_neon/uint8x8x3_t
- arm_neon/vzip_f32
- armintr/_arm_ssub8
- arm_neon/uint16x4x4_t
- armintr/__swi
- armintr/_arm_smlatb
- arm_neon/vrhaddq_s8
- arm_neon/vpmax_s32
- arm_neon/vqshl_s64
- arm_neon/vrev16q_p8
- arm_neon/vqmovn_u32
- arm_neon/vld1q_f16
- arm_neon/vornq_u64
- arm_neon/vqshlq_n_s16
- arm_neon/vld1_f16
- armintr/_arm_smmlsr
- arm_neon/vshlq_s16
- arm_neon/vsubhn_s16
- arm_neon/vmulq_p8
- arm_neon/vdupq_lane_f32
- armintr/_arm_shadd16
- arm_neon/vornq_s16
- arm_neon/vst1q_lane_u8
- arm_neon/vcaleq_f32
- arm_neon/vst3q_lane_f16
- armintr/_arm_sdiv
- arm_neon/vld2_u16
- arm_neon/vdup_lane_u16
- arm_neon/vst4q_lane_f32
- arm_neon/vdup_n_f32
- arm_neon/vsubq_u8
- arm_neon/vset_lane_p16
- arm_neon/vrsqrte_f32
- arm_neon/vsubl_u8
- arm_neon/vld3q_lane_f32
- arm_neon/vqnegq_s8
- arm_neon/vqmovn_s16
- arm_neon/int16x8x3_t
- arm_neon/veorq_u16
- arm_neon/vqdmulh_n_s16
- arm_neon/vhaddq_u8
- arm_neon/vpadal_u8
- arm_neon/vst2q_s16
- arm_neon/poly16x8x4_t
- arm_neon/int64x2_t
- arm_neon/vmull_s32
- arm_neon/vld4_lane_s32
- arm_neon/vst4q_p8
- arm_neon/vmlal_lane_u16
- arm_neon/vclz_u32
- arm_neon/vsliq_n_s8
- arm_neon/vmls_n_f32
- arm_neon/vmlsl_lane_s16
- arm_neon/vst4q_u32
- arm_neon/vld1q_lane_s16
- arm_neon/vst1q_f32
- arm_neon/vrshr_n_u8
- arm_neon/vst1q_s64
- arm_neon/vbslq_u32
- arm_neon/vset_lane_s8
- arm_neon/vdupq_lane_p16
- arm_neon/vtstq_s16
- arm_neon/vshl_n_s8
- arm_neon/vqrdmulhq_n_s16
- arm_neon/vget_high_f16
- arm_neon/vst4_lane_u32
- arm_neon/vraddhn_s16
- arm_neon/vmlsl_lane_s32
- arm_neon/vld3q_s32
- arm_neon/vsriq_n_u64
- arm_neon/vld4_dup_u8
- arm_neon/vld4q_s8
- arm_neon/vqmovn_s64
- arm_neon/vrev32q_p8
- arm_neon/vsliq_n_p8
- arm_neon/vzipq_s16
- arm_neon/vgetq_lane_s64
- arm_neon/vst4_p16
- arm_neon/vsubq_u16
- arm_neon/vrev64_s32
- armintr/_arm_uhadd8
- arm_neon/vornq_u16
- arm_neon/vst4_lane_s8
- arm_neon/vabd_s32
- arm_neon/vqrdmulhq_s16
- arm_neon/vqshlq_s32
- arm_neon/int64x2x4_t
- arm_neon/vset_lane_u16
- arm_neon/vrsra_n_s32
- arm_neon/vabdl_u16
- arm_neon/vsliq_n_s32
helpviewer_keywords:
- cl.exe compiler, ARM intrinsics
- intrinsics, ARM
- __cps ARM intrinsic
- __dmb ARM intrinsic
- __dsb ARM intrinsic
- __emit ARM intrinsic
- __hvc ARM intrinsic
- __isb ARM intrinsic
- __iso_volatile_load16 ARM intrinsic
- __iso_volatile_load32 ARM intrinsic
- __iso_volatile_load64 ARM intrinsic
- __iso_volatile_load8 ARM intrinsic
- __iso_volatile_store16 ARM intrinsic
- __iso_volatile_store32 ARM intrinsic
- __iso_volatile_store64 ARM intrinsic
- __iso_volatile_store8 ARM intrinsic
- __ldrexd ARM intrinsic
- __prefetch ARM intrinsic
- __rdpmccntr64 ARM intrinsic
- __sev ARM intrinsic
- __static_assert ARM intrinsic
- __swi ARM intrinsic
- __trap ARM intrinsic
- __wfe ARM intrinsic
- __wfi ARM intrinsic
- _AddSatInt ARM intrinsic
- _arm_bfc ARM intrinsic
- _arm_bfi ARM intrinsic
- _arm_clz ARM intrinsic
- _arm_pkhbt ARM intrinsic
- _arm_pkhtb ARM intrinsic
- _arm_qadd ARM intrinsic
- _arm_qadd16 ARM intrinsic
- _arm_qadd8 ARM intrinsic
- _arm_qasx ARM intrinsic
- _arm_qdadd ARM intrinsic
- _arm_qdsub ARM intrinsic
- _arm_qsax ARM intrinsic
- _arm_qsub ARM intrinsic
- _arm_qsub16 ARM intrinsic
- _arm_qsub8 ARM intrinsic
- _arm_rbit ARM intrinsic
- _arm_rev ARM intrinsic
- _arm_rev16 ARM intrinsic
- _arm_revsh ARM intrinsic
- _arm_sadd16 ARM intrinsic
- _arm_sadd8 ARM intrinsic
- _arm_sasx ARM intrinsic
- _arm_sbfx ARM intrinsic
- _arm_sdiv ARM intrinsic
- _arm_shadd16 ARM intrinsic
- _arm_shadd8 ARM intrinsic
- _arm_shasx ARM intrinsic
- _arm_shsax ARM intrinsic
- _arm_shsub16 ARM intrinsic
- _arm_shsub8 ARM intrinsic
- _arm_smlabb ARM intrinsic
- _arm_smlabt ARM intrinsic
- _arm_smlad ARM intrinsic
- _arm_smladx ARM intrinsic
- _arm_smlal ARM intrinsic
- _arm_smlalbb ARM intrinsic
- _arm_smlalbt ARM intrinsic
- _arm_smlald ARM intrinsic
- _arm_smlaldx ARM intrinsic
- _arm_smlaltb ARM intrinsic
- _arm_smlaltt ARM intrinsic
- _arm_smlatb ARM intrinsic
- _arm_smlatt ARM intrinsic
- _arm_smlawb ARM intrinsic
- _arm_smlawt ARM intrinsic
- _arm_smlsd ARM intrinsic
- _arm_smlsdx ARM intrinsic
- _arm_smlsld ARM intrinsic
- _arm_smlsldx ARM intrinsic
- _arm_smmla ARM intrinsic
- _arm_smmlar ARM intrinsic
- _arm_smmls ARM intrinsic
- _arm_smmlsr ARM intrinsic
- _arm_smmul ARM intrinsic
- _arm_smmulr ARM intrinsic
- _arm_smuad ARM intrinsic
- _arm_smuadx ARM intrinsic
- _arm_smulbb ARM intrinsic
- _arm_smulbt ARM intrinsic
- _arm_smull ARM intrinsic
- _arm_smultb ARM intrinsic
- _arm_smultt ARM intrinsic
- _arm_smulwb ARM intrinsic
- _arm_smulwt ARM intrinsic
- _arm_smusd ARM intrinsic
- _arm_smusdx ARM intrinsic
- _arm_ssat ARM intrinsic
- _arm_ssat16 ARM intrinsic
- _arm_ssax ARM intrinsic
- _arm_ssub16 ARM intrinsic
- _arm_ssub8 ARM intrinsic
- _arm_sxtab ARM intrinsic
- _arm_sxtab16 ARM intrinsic
- _arm_sxtah ARM intrinsic
- _arm_sxtb ARM intrinsic
- _arm_sxtb16 ARM intrinsic
- _arm_sxth ARM intrinsic
- _arm_uadd16 ARM intrinsic
- _arm_uadd8 ARM intrinsic
- _arm_uasx ARM intrinsic
- _arm_ubfx ARM intrinsic
- _arm_udiv ARM intrinsic
- _arm_uhadd16 ARM intrinsic
- _arm_uhadd8 ARM intrinsic
- _arm_uhasx ARM intrinsic
- _arm_uhsax ARM intrinsic
- _arm_uhsub16 ARM intrinsic
- _arm_uhsub8 ARM intrinsic
- _arm_umaal ARM intrinsic
- _arm_umlal ARM intrinsic
- _arm_umull ARM intrinsic
- _arm_uqadd16 ARM intrinsic
- _arm_uqadd8 ARM intrinsic
- _arm_uqasx ARM intrinsic
- _arm_uqsax ARM intrinsic
- _arm_uqsub16 ARM intrinsic
- _arm_uqsub8 ARM intrinsic
- _arm_usad8 ARM intrinsic
- _arm_usada8 ARM intrinsic
- _arm_usat ARM intrinsic
- _arm_usat16 ARM intrinsic
- _arm_usax ARM intrinsic
- _arm_usub16 ARM intrinsic
- _arm_usub8 ARM intrinsic
- _arm_uxtab ARM intrinsic
- _arm_uxtab16 ARM intrinsic
- _arm_uxtah ARM intrinsic
- _arm_uxtb ARM intrinsic
- _arm_uxtb16 ARM intrinsic
- _arm_uxth ARM intrinsic
- _CopyDoubleFromInt64 ARM intrinsic
- _CopyFloatFromInt32 ARM intrinsic
- _CopyInt32FromFloat ARM intrinsic
- _CopyInt64FromDouble ARM intrinsic
- _CountLeadingOnes ARM intrinsic
- _CountLeadingOnes64 ARM intrinsic
- _CountLeadingSigns ARM intrinsic
- _CountLeadingSigns64 ARM intrinsic
- _CountLeadingZeros ARM intrinsic
- _CountLeadingZeros64 ARM intrinsic
- _CountOneBits ARM intrinsic
- _CountOneBits64 ARM intrinsic
- _DAddSatInt ARM intrinsic
- _DSubSatInt ARM intrinsic
- _isunordered ARM intrinsic
- _isunorderedf ARM intrinsic
- _MoveFromCoprocessor ARM intrinsic
- _MoveFromCoprocessor2 ARM intrinsic
- _MoveFromCoprocessor64 ARM intrinsic
- _MoveToCoprocessor ARM intrinsic
- _MoveToCoprocessor2 ARM intrinsic
- _MoveToCoprocessor64 ARM intrinsic
- _MulHigh ARM intrinsic
- _MulUnsignedHigh ARM intrinsic
- _ReadBankedReg ARM intrinsic
- _ReadStatusReg ARM intrinsic
- _SubSatInt ARM intrinsic
- _WriteBankedReg ARM intrinsic
- _WriteStatusReg ARM intrinsic
- float32x2_t ARM intrinsic
- float32x2x2_t ARM intrinsic
- float32x2x3_t ARM intrinsic
- float32x2x4_t ARM intrinsic
- float32x4_t ARM intrinsic
- float32x4x2_t ARM intrinsic
- float32x4x3_t ARM intrinsic
- float32x4x4_t ARM intrinsic
- int16x4_t ARM intrinsic
- int16x4x2_t ARM intrinsic
- int16x4x3_t ARM intrinsic
- int16x4x4_t ARM intrinsic
- int16x8_t ARM intrinsic
- int16x8x2_t ARM intrinsic
- int16x8x3_t ARM intrinsic
- int16x8x4_t ARM intrinsic
- int32x2_t ARM intrinsic
- int32x2x2_t ARM intrinsic
- int32x2x3_t ARM intrinsic
- int32x2x4_t ARM intrinsic
- int32x4_t ARM intrinsic
- int32x4x2_t ARM intrinsic
- int32x4x3_t ARM intrinsic
- int32x4x4_t ARM intrinsic
- int64x1_t ARM intrinsic
- int64x1x2_t ARM intrinsic
- int64x1x3_t ARM intrinsic
- int64x1x4_t ARM intrinsic
- int64x2_t ARM intrinsic
- int64x2x2_t ARM intrinsic
- int64x2x3_t ARM intrinsic
- int64x2x4_t ARM intrinsic
- int8x16_t ARM intrinsic
- int8x16x2_t ARM intrinsic
- int8x16x3_t ARM intrinsic
- int8x16x4_t ARM intrinsic
- int8x8_t ARM intrinsic
- int8x8x2_t ARM intrinsic
- int8x8x3_t ARM intrinsic
- int8x8x4_t ARM intrinsic
- poly16_t ARM intrinsic
- poly16x4_t ARM intrinsic
- poly16x4x2_t ARM intrinsic
- poly16x4x3_t ARM intrinsic
- poly16x4x4_t ARM intrinsic
- poly16x8_t ARM intrinsic
- poly16x8x2_t ARM intrinsic
- poly16x8x3_t ARM intrinsic
- poly16x8x4_t ARM intrinsic
- poly8_t ARM intrinsic
- poly8x16_t ARM intrinsic
- poly8x16x2_t ARM intrinsic
- poly8x16x3_t ARM intrinsic
- poly8x16x4_t ARM intrinsic
- poly8x8_t ARM intrinsic
- poly8x8x2_t ARM intrinsic
- poly8x8x3_t ARM intrinsic
- poly8x8x4_t ARM intrinsic
- uint16x4_t ARM intrinsic
- uint16x4x2_t ARM intrinsic
- uint16x4x3_t ARM intrinsic
- uint16x4x4_t ARM intrinsic
- uint16x8_t ARM intrinsic
- uint16x8x2_t ARM intrinsic
- uint16x8x3_t ARM intrinsic
- uint16x8x4_t ARM intrinsic
- uint32x2_t ARM intrinsic
- uint32x2x2_t ARM intrinsic
- uint32x2x3_t ARM intrinsic
- uint32x2x4_t ARM intrinsic
- uint32x4_t ARM intrinsic
- uint32x4x2_t ARM intrinsic
- uint32x4x3_t ARM intrinsic
- uint32x4x4_t ARM intrinsic
- uint64x1_t ARM intrinsic
- uint64x1x2_t ARM intrinsic
- uint64x1x3_t ARM intrinsic
- uint64x1x4_t ARM intrinsic
- uint64x2_t ARM intrinsic
- uint64x2x2_t ARM intrinsic
- uint64x2x3_t ARM intrinsic
- uint64x2x4_t ARM intrinsic
- uint8x16_t ARM intrinsic
- uint8x16x2_t ARM intrinsic
- uint8x16x3_t ARM intrinsic
- uint8x16x4_t ARM intrinsic
- uint8x8_t ARM intrinsic
- uint8x8x2_t ARM intrinsic
- uint8x8x3_t ARM intrinsic
- uint8x8x4_t ARM intrinsic
- vaba_s16 ARM intrinsic
- vaba_s32 ARM intrinsic
- vaba_s8 ARM intrinsic
- vaba_u16 ARM intrinsic
- vaba_u32 ARM intrinsic
- vaba_u8 ARM intrinsic
- vabal_s16 ARM intrinsic
- vabal_s32 ARM intrinsic
- vabal_s8 ARM intrinsic
- vabal_u16 ARM intrinsic
- vabal_u32 ARM intrinsic
- vabal_u8 ARM intrinsic
- vabaq_s16 ARM intrinsic
- vabaq_s32 ARM intrinsic
- vabaq_s8 ARM intrinsic
- vabaq_u16 ARM intrinsic
- vabaq_u32 ARM intrinsic
- vabaq_u8 ARM intrinsic
- vabd_f32 ARM intrinsic
- vabd_s16 ARM intrinsic
- vabd_s32 ARM intrinsic
- vabd_s8 ARM intrinsic
- vabd_u16 ARM intrinsic
- vabd_u32 ARM intrinsic
- vabd_u8 ARM intrinsic
- vabdl_s16 ARM intrinsic
- vabdl_s32 ARM intrinsic
- vabdl_s8 ARM intrinsic
- vabdl_u16 ARM intrinsic
- vabdl_u32 ARM intrinsic
- vabdl_u8 ARM intrinsic
- vabdq_f32 ARM intrinsic
- vabdq_s16 ARM intrinsic
- vabdq_s32 ARM intrinsic
- vabdq_s8 ARM intrinsic
- vabdq_u16 ARM intrinsic
- vabdq_u32 ARM intrinsic
- vabdq_u8 ARM intrinsic
- vabs_f32 ARM intrinsic
- vabs_s16 ARM intrinsic
- vabs_s32 ARM intrinsic
- vabs_s8 ARM intrinsic
- vabsq_f32 ARM intrinsic
- vabsq_s16 ARM intrinsic
- vabsq_s32 ARM intrinsic
- vabsq_s8 ARM intrinsic
- vadd_f32 ARM intrinsic
- vadd_s16 ARM intrinsic
- vadd_s32 ARM intrinsic
- vadd_s64 ARM intrinsic
- vadd_s8 ARM intrinsic
- vadd_u16 ARM intrinsic
- vadd_u32 ARM intrinsic
- vadd_u64 ARM intrinsic
- vadd_u8 ARM intrinsic
- vaddhn_s16 ARM intrinsic
- vaddhn_s32 ARM intrinsic
- vaddhn_s64 ARM intrinsic
- vaddhn_u16 ARM intrinsic
- vaddhn_u32 ARM intrinsic
- vaddhn_u64 ARM intrinsic
- vaddl_s16 ARM intrinsic
- vaddl_s32 ARM intrinsic
- vaddl_s8 ARM intrinsic
- vaddl_u16 ARM intrinsic
- vaddl_u32 ARM intrinsic
- vaddl_u8 ARM intrinsic
- vaddq_f32 ARM intrinsic
- vaddq_s16 ARM intrinsic
- vaddq_s32 ARM intrinsic
- vaddq_s64 ARM intrinsic
- vaddq_s8 ARM intrinsic
- vaddq_u16 ARM intrinsic
- vaddq_u32 ARM intrinsic
- vaddq_u64 ARM intrinsic
- vaddq_u8 ARM intrinsic
- vaddw_s16 ARM intrinsic
- vaddw_s32 ARM intrinsic
- vaddw_s8 ARM intrinsic
- vaddw_u16 ARM intrinsic
- vaddw_u32 ARM intrinsic
- vaddw_u8 ARM intrinsic
- vand_s16 ARM intrinsic
- vand_s32 ARM intrinsic
- vand_s64 ARM intrinsic
- vand_s8 ARM intrinsic
- vand_u16 ARM intrinsic
- vand_u32 ARM intrinsic
- vand_u64 ARM intrinsic
- vand_u8 ARM intrinsic
- vandq_s16 ARM intrinsic
- vandq_s32 ARM intrinsic
- vandq_s64 ARM intrinsic
- vandq_s8 ARM intrinsic
- vandq_u16 ARM intrinsic
- vandq_u32 ARM intrinsic
- vandq_u64 ARM intrinsic
- vandq_u8 ARM intrinsic
- vbic_s16 ARM intrinsic
- vbic_s32 ARM intrinsic
- vbic_s64 ARM intrinsic
- vbic_s8 ARM intrinsic
- vbic_u16 ARM intrinsic
- vbic_u32 ARM intrinsic
- vbic_u64 ARM intrinsic
- vbic_u8 ARM intrinsic
- vbicq_s16 ARM intrinsic
- vbicq_s32 ARM intrinsic
- vbicq_s64 ARM intrinsic
- vbicq_s8 ARM intrinsic
- vbicq_u16 ARM intrinsic
- vbicq_u32 ARM intrinsic
- vbicq_u64 ARM intrinsic
- vbicq_u8 ARM intrinsic
- vbsl_f32 ARM intrinsic
- vbsl_p16 ARM intrinsic
- vbsl_p8 ARM intrinsic
- vbsl_s16 ARM intrinsic
- vbsl_s32 ARM intrinsic
- vbsl_s64 ARM intrinsic
- vbsl_s8 ARM intrinsic
- vbsl_u16 ARM intrinsic
- vbsl_u32 ARM intrinsic
- vbsl_u64 ARM intrinsic
- vbsl_u8 ARM intrinsic
- vbslq_f32 ARM intrinsic
- vbslq_p16 ARM intrinsic
- vbslq_p8 ARM intrinsic
- vbslq_s16 ARM intrinsic
- vbslq_s32 ARM intrinsic
- vbslq_s64 ARM intrinsic
- vbslq_s8 ARM intrinsic
- vbslq_u16 ARM intrinsic
- vbslq_u32 ARM intrinsic
- vbslq_u64 ARM intrinsic
- vbslq_u8 ARM intrinsic
- vcage_f32 ARM intrinsic
- vcageq_f32 ARM intrinsic
- vcagt_f32 ARM intrinsic
- vcagtq_f32 ARM intrinsic
- vcale_f32 ARM intrinsic
- vcaleq_f32 ARM intrinsic
- vcalt_f32 ARM intrinsic
- vcaltq_f32 ARM intrinsic
- vceq_f32 ARM intrinsic
- vceq_p8 ARM intrinsic
- vceq_s16 ARM intrinsic
- vceq_s32 ARM intrinsic
- vceq_s8 ARM intrinsic
- vceq_u16 ARM intrinsic
- vceq_u32 ARM intrinsic
- vceq_u8 ARM intrinsic
- vceqq_f32 ARM intrinsic
- vceqq_p8 ARM intrinsic
- vceqq_s16 ARM intrinsic
- vceqq_s32 ARM intrinsic
- vceqq_s8 ARM intrinsic
- vceqq_u16 ARM intrinsic
- vceqq_u32 ARM intrinsic
- vceqq_u8 ARM intrinsic
- vcge_f32 ARM intrinsic
- vcge_s16 ARM intrinsic
- vcge_s32 ARM intrinsic
- vcge_s8 ARM intrinsic
- vcge_u16 ARM intrinsic
- vcge_u32 ARM intrinsic
- vcge_u8 ARM intrinsic
- vcgeq_f32 ARM intrinsic
- vcgeq_s16 ARM intrinsic
- vcgeq_s32 ARM intrinsic
- vcgeq_s8 ARM intrinsic
- vcgeq_u16 ARM intrinsic
- vcgeq_u32 ARM intrinsic
- vcgeq_u8 ARM intrinsic
- vcgt_f32 ARM intrinsic
- vcgt_s16 ARM intrinsic
- vcgt_s32 ARM intrinsic
- vcgt_s8 ARM intrinsic
- vcgt_u16 ARM intrinsic
- vcgt_u32 ARM intrinsic
- vcgt_u8 ARM intrinsic
- vcgtq_f32 ARM intrinsic
- vcgtq_s16 ARM intrinsic
- vcgtq_s32 ARM intrinsic
- vcgtq_s8 ARM intrinsic
- vcgtq_u16 ARM intrinsic
- vcgtq_u32 ARM intrinsic
- vcgtq_u8 ARM intrinsic
- vcle_f32 ARM intrinsic
- vcle_s16 ARM intrinsic
- vcle_s32 ARM intrinsic
- vcle_s8 ARM intrinsic
- vcle_u16 ARM intrinsic
- vcle_u32 ARM intrinsic
- vcle_u8 ARM intrinsic
- vcleq_f32 ARM intrinsic
- vcleq_s16 ARM intrinsic
- vcleq_s32 ARM intrinsic
- vcleq_s8 ARM intrinsic
- vcleq_u16 ARM intrinsic
- vcleq_u32 ARM intrinsic
- vcleq_u8 ARM intrinsic
- vcls_s16 ARM intrinsic
- vcls_s32 ARM intrinsic
- vcls_s8 ARM intrinsic
- vclsq_s16 ARM intrinsic
- vclsq_s32 ARM intrinsic
- vclsq_s8 ARM intrinsic
- vclt_f32 ARM intrinsic
- vclt_s16 ARM intrinsic
- vclt_s32 ARM intrinsic
- vclt_s8 ARM intrinsic
- vclt_u16 ARM intrinsic
- vclt_u32 ARM intrinsic
- vclt_u8 ARM intrinsic
- vcltq_f32 ARM intrinsic
- vcltq_s16 ARM intrinsic
- vcltq_s32 ARM intrinsic
- vcltq_s8 ARM intrinsic
- vcltq_u16 ARM intrinsic
- vcltq_u32 ARM intrinsic
- vcltq_u8 ARM intrinsic
- vclz_s16 ARM intrinsic
- vclz_s32 ARM intrinsic
- vclz_s8 ARM intrinsic
- vclz_u16 ARM intrinsic
- vclz_u32 ARM intrinsic
- vclz_u8 ARM intrinsic
- vclzq_s16 ARM intrinsic
- vclzq_s32 ARM intrinsic
- vclzq_s8 ARM intrinsic
- vclzq_u16 ARM intrinsic
- vclzq_u32 ARM intrinsic
- vclzq_u8 ARM intrinsic
- vcnt_p8 ARM intrinsic
- vcnt_s8 ARM intrinsic
- vcnt_u8 ARM intrinsic
- vcntq_p8 ARM intrinsic
- vcntq_s8 ARM intrinsic
- vcntq_u8 ARM intrinsic
- vcombine_f16 ARM intrinsic
- vcombine_f32 ARM intrinsic
- vcombine_p16 ARM intrinsic
- vcombine_p8 ARM intrinsic
- vcombine_s16 ARM intrinsic
- vcombine_s32 ARM intrinsic
- vcombine_s64 ARM intrinsic
- vcombine_s8 ARM intrinsic
- vcombine_u16 ARM intrinsic
- vcombine_u32 ARM intrinsic
- vcombine_u64 ARM intrinsic
- vcombine_u8 ARM intrinsic
- vcreate_f16 ARM intrinsic
- vcreate_f32 ARM intrinsic
- vcreate_p16 ARM intrinsic
- vcreate_p8 ARM intrinsic
- vcreate_s16 ARM intrinsic
- vcreate_s32 ARM intrinsic
- vcreate_s64 ARM intrinsic
- vcreate_s8 ARM intrinsic
- vcreate_u16 ARM intrinsic
- vcreate_u32 ARM intrinsic
- vcreate_u64 ARM intrinsic
- vcreate_u8 ARM intrinsic
- vcvt_f16_f32 ARM intrinsic
- vcvt_f32_f16 ARM intrinsic
- vcvt_f32_s32 ARM intrinsic
- vcvt_f32_u32 ARM intrinsic
- vcvt_n_f32_s32 ARM intrinsic
- vcvt_n_f32_u32 ARM intrinsic
- vcvt_n_s32_f32 ARM intrinsic
- vcvt_n_u32_f32 ARM intrinsic
- vcvt_s32_f32 ARM intrinsic
- vcvt_u32_f32 ARM intrinsic
- vcvtq_f32_s32 ARM intrinsic
- vcvtq_f32_u32 ARM intrinsic
- vcvtq_n_f32_s32 ARM intrinsic
- vcvtq_n_f32_u32 ARM intrinsic
- vcvtq_n_s32_f32 ARM intrinsic
- vcvtq_n_u32_f32 ARM intrinsic
- vcvtq_s32_f32 ARM intrinsic
- vcvtq_u32_f32 ARM intrinsic
- vdup_lane_f32 ARM intrinsic
- vdup_lane_p16 ARM intrinsic
- vdup_lane_p8 ARM intrinsic
- vdup_lane_s16 ARM intrinsic
- vdup_lane_s32 ARM intrinsic
- vdup_lane_s64 ARM intrinsic
- vdup_lane_s8 ARM intrinsic
- vdup_lane_u16 ARM intrinsic
- vdup_lane_u32 ARM intrinsic
- vdup_lane_u64 ARM intrinsic
- vdup_lane_u8 ARM intrinsic
- vdup_n_f32 ARM intrinsic
- vdup_n_p16 ARM intrinsic
- vdup_n_p8 ARM intrinsic
- vdup_n_s16 ARM intrinsic
- vdup_n_s32 ARM intrinsic
- vdup_n_s64 ARM intrinsic
- vdup_n_s8 ARM intrinsic
- vdup_n_u16 ARM intrinsic
- vdup_n_u32 ARM intrinsic
- vdup_n_u64 ARM intrinsic
- vdup_n_u8 ARM intrinsic
- vdupq_lane_f32 ARM intrinsic
- vdupq_lane_p16 ARM intrinsic
- vdupq_lane_p8 ARM intrinsic
- vdupq_lane_s16 ARM intrinsic
- vdupq_lane_s32 ARM intrinsic
- vdupq_lane_s64 ARM intrinsic
- vdupq_lane_s8 ARM intrinsic
- vdupq_lane_u16 ARM intrinsic
- vdupq_lane_u32 ARM intrinsic
- vdupq_lane_u64 ARM intrinsic
- vdupq_lane_u8 ARM intrinsic
- vdupq_n_f32 ARM intrinsic
- vdupq_n_p16 ARM intrinsic
- vdupq_n_p8 ARM intrinsic
- vdupq_n_s16 ARM intrinsic
- vdupq_n_s32 ARM intrinsic
- vdupq_n_s64 ARM intrinsic
- vdupq_n_s8 ARM intrinsic
- vdupq_n_u16 ARM intrinsic
- vdupq_n_u32 ARM intrinsic
- vdupq_n_u64 ARM intrinsic
- vdupq_n_u8 ARM intrinsic
- veor_s16 ARM intrinsic
- veor_s32 ARM intrinsic
- veor_s64 ARM intrinsic
- veor_s8 ARM intrinsic
- veor_u16 ARM intrinsic
- veor_u32 ARM intrinsic
- veor_u64 ARM intrinsic
- veor_u8 ARM intrinsic
- veorq_s16 ARM intrinsic
- veorq_s32 ARM intrinsic
- veorq_s64 ARM intrinsic
- veorq_s8 ARM intrinsic
- veorq_u16 ARM intrinsic
- veorq_u32 ARM intrinsic
- veorq_u64 ARM intrinsic
- veorq_u8 ARM intrinsic
- vext_p16 ARM intrinsic
- vext_p8 ARM intrinsic
- vext_s16 ARM intrinsic
- vext_s32 ARM intrinsic
- vext_s64 ARM intrinsic
- vext_s8 ARM intrinsic
- vext_u16 ARM intrinsic
- vext_u32 ARM intrinsic
- vext_u64 ARM intrinsic
- vext_u8 ARM intrinsic
- vextq_p16 ARM intrinsic
- vextq_p8 ARM intrinsic
- vextq_s16 ARM intrinsic
- vextq_s32 ARM intrinsic
- vextq_s64 ARM intrinsic
- vextq_s8 ARM intrinsic
- vextq_u16 ARM intrinsic
- vextq_u32 ARM intrinsic
- vextq_u64 ARM intrinsic
- vextq_u8 ARM intrinsic
- vget_high_f16 ARM intrinsic
- vget_high_f32 ARM intrinsic
- vget_high_p16 ARM intrinsic
- vget_high_p8 ARM intrinsic
- vget_high_s16 ARM intrinsic
- vget_high_s32 ARM intrinsic
- vget_high_s64 ARM intrinsic
- vget_high_s8 ARM intrinsic
- vget_high_u16 ARM intrinsic
- vget_high_u32 ARM intrinsic
- vget_high_u64 ARM intrinsic
- vget_high_u8 ARM intrinsic
- vget_lane_f32 ARM intrinsic
- vget_lane_p16 ARM intrinsic
- vget_lane_p8 ARM intrinsic
- vget_lane_s16 ARM intrinsic
- vget_lane_s32 ARM intrinsic
- vget_lane_s64 ARM intrinsic
- vget_lane_s8 ARM intrinsic
- vget_lane_u16 ARM intrinsic
- vget_lane_u32 ARM intrinsic
- vget_lane_u64 ARM intrinsic
- vget_lane_u8 ARM intrinsic
- vget_low_f16 ARM intrinsic
- vget_low_f32 ARM intrinsic
- vget_low_p16 ARM intrinsic
- vget_low_p8 ARM intrinsic
- vget_low_s16 ARM intrinsic
- vget_low_s32 ARM intrinsic
- vget_low_s64 ARM intrinsic
- vget_low_s8 ARM intrinsic
- vget_low_u16 ARM intrinsic
- vget_low_u32 ARM intrinsic
- vget_low_u64 ARM intrinsic
- vget_low_u8 ARM intrinsic
- vgetq_lane_f32 ARM intrinsic
- vgetq_lane_p16 ARM intrinsic
- vgetq_lane_p8 ARM intrinsic
- vgetq_lane_s16 ARM intrinsic
- vgetq_lane_s32 ARM intrinsic
- vgetq_lane_s64 ARM intrinsic
- vgetq_lane_s8 ARM intrinsic
- vgetq_lane_u16 ARM intrinsic
- vgetq_lane_u32 ARM intrinsic
- vgetq_lane_u64 ARM intrinsic
- vgetq_lane_u8 ARM intrinsic
- vhadd_s16 ARM intrinsic
- vhadd_s32 ARM intrinsic
- vhadd_s8 ARM intrinsic
- vhadd_u16 ARM intrinsic
- vhadd_u32 ARM intrinsic
- vhadd_u8 ARM intrinsic
- vhaddq_s16 ARM intrinsic
- vhaddq_s32 ARM intrinsic
- vhaddq_s8 ARM intrinsic
- vhaddq_u16 ARM intrinsic
- vhaddq_u32 ARM intrinsic
- vhaddq_u8 ARM intrinsic
- vhsub_s16 ARM intrinsic
- vhsub_s32 ARM intrinsic
- vhsub_s8 ARM intrinsic
- vhsub_u16 ARM intrinsic
- vhsub_u32 ARM intrinsic
- vhsub_u8 ARM intrinsic
- vhsubq_s16 ARM intrinsic
- vhsubq_s32 ARM intrinsic
- vhsubq_s8 ARM intrinsic
- vhsubq_u16 ARM intrinsic
- vhsubq_u32 ARM intrinsic
- vhsubq_u8 ARM intrinsic
- vld1_dup_f16 ARM intrinsic
- vld1_dup_f32 ARM intrinsic
- vld1_dup_p16 ARM intrinsic
- vld1_dup_p8 ARM intrinsic
- vld1_dup_s16 ARM intrinsic
- vld1_dup_s32 ARM intrinsic
- vld1_dup_s64 ARM intrinsic
- vld1_dup_s8 ARM intrinsic
- vld1_dup_u16 ARM intrinsic
- vld1_dup_u32 ARM intrinsic
- vld1_dup_u64 ARM intrinsic
- vld1_dup_u8 ARM intrinsic
- vld1_f16 ARM intrinsic
- vld1_f32 ARM intrinsic
- vld1_lane_f32 ARM intrinsic
- vld1_lane_p16 ARM intrinsic
- vld1_lane_p8 ARM intrinsic
- vld1_lane_s16 ARM intrinsic
- vld1_lane_s32 ARM intrinsic
- vld1_lane_s64 ARM intrinsic
- vld1_lane_s8 ARM intrinsic
- vld1_lane_u16 ARM intrinsic
- vld1_lane_u32 ARM intrinsic
- vld1_lane_u64 ARM intrinsic
- vld1_lane_u8 ARM intrinsic
- vld1_p16 ARM intrinsic
- vld1_p8 ARM intrinsic
- vld1_s16 ARM intrinsic
- vld1_s32 ARM intrinsic
- vld1_s64 ARM intrinsic
- vld1_s8 ARM intrinsic
- vld1_u16 ARM intrinsic
- vld1_u32 ARM intrinsic
- vld1_u64 ARM intrinsic
- vld1_u8 ARM intrinsic
- vld1q_dup_f16 ARM intrinsic
- vld1q_dup_f32 ARM intrinsic
- vld1q_dup_p16 ARM intrinsic
- vld1q_dup_p8 ARM intrinsic
- vld1q_dup_s16 ARM intrinsic
- vld1q_dup_s32 ARM intrinsic
- vld1q_dup_s64 ARM intrinsic
- vld1q_dup_s8 ARM intrinsic
- vld1q_dup_u16 ARM intrinsic
- vld1q_dup_u32 ARM intrinsic
- vld1q_dup_u64 ARM intrinsic
- vld1q_dup_u8 ARM intrinsic
- vld1q_f16 ARM intrinsic
- vld1q_f32 ARM intrinsic
- vld1q_lane_f16 ARM intrinsic
- vld1q_lane_f32 ARM intrinsic
- vld1q_lane_p16 ARM intrinsic
- vld1q_lane_p8 ARM intrinsic
- vld1q_lane_s16 ARM intrinsic
- vld1q_lane_s32 ARM intrinsic
- vld1q_lane_s64 ARM intrinsic
- vld1q_lane_s8 ARM intrinsic
- vld1q_lane_u16 ARM intrinsic
- vld1q_lane_u32 ARM intrinsic
- vld1q_lane_u64 ARM intrinsic
- vld1q_lane_u8 ARM intrinsic
- vld1q_p16 ARM intrinsic
- vld1q_p8 ARM intrinsic
- vld1q_s16 ARM intrinsic
- vld1q_s32 ARM intrinsic
- vld1q_s64 ARM intrinsic
- vld1q_s8 ARM intrinsic
- vld1q_u16 ARM intrinsic
- vld1q_u32 ARM intrinsic
- vld1q_u64 ARM intrinsic
- vld1q_u8 ARM intrinsic
- vld2_dup_f16 ARM intrinsic
- vld2_dup_f32 ARM intrinsic
- vld2_dup_p16 ARM intrinsic
- vld2_dup_p8 ARM intrinsic
- vld2_dup_s16 ARM intrinsic
- vld2_dup_s32 ARM intrinsic
- vld2_dup_s64 ARM intrinsic
- vld2_dup_s8 ARM intrinsic
- vld2_dup_u16 ARM intrinsic
- vld2_dup_u32 ARM intrinsic
- vld2_dup_u64 ARM intrinsic
- vld2_dup_u8 ARM intrinsic
- vld2_f16 ARM intrinsic
- vld2_f32 ARM intrinsic
- vld2_lane_f16 ARM intrinsic
- vld2_lane_f32 ARM intrinsic
- vld2_lane_p16 ARM intrinsic
- vld2_lane_p8 ARM intrinsic
- vld2_lane_s16 ARM intrinsic
- vld2_lane_s32 ARM intrinsic
- vld2_lane_s8 ARM intrinsic
- vld2_lane_u16 ARM intrinsic
- vld2_lane_u32 ARM intrinsic
- vld2_lane_u8 ARM intrinsic
- vld2_p16 ARM intrinsic
- vld2_p8 ARM intrinsic
- vld2_s16 ARM intrinsic
- vld2_s32 ARM intrinsic
- vld2_s64 ARM intrinsic
- vld2_s8 ARM intrinsic
- vld2_u16 ARM intrinsic
- vld2_u32 ARM intrinsic
- vld2_u64 ARM intrinsic
- vld2_u8 ARM intrinsic
- vld2q_f16 ARM intrinsic
- vld2q_f32 ARM intrinsic
- vld2q_lane_f16 ARM intrinsic
- vld2q_lane_f32 ARM intrinsic
- vld2q_lane_p16 ARM intrinsic
- vld2q_lane_s16 ARM intrinsic
- vld2q_lane_s32 ARM intrinsic
- vld2q_lane_u16 ARM intrinsic
- vld2q_lane_u32 ARM intrinsic
- vld2q_p16 ARM intrinsic
- vld2q_p8 ARM intrinsic
- vld2q_s16 ARM intrinsic
- vld2q_s32 ARM intrinsic
- vld2q_s8 ARM intrinsic
- vld2q_u16 ARM intrinsic
- vld2q_u32 ARM intrinsic
- vld2q_u8 ARM intrinsic
- vld3_dup_f16 ARM intrinsic
- vld3_dup_f32 ARM intrinsic
- vld3_dup_p16 ARM intrinsic
- vld3_dup_p8 ARM intrinsic
- vld3_dup_s16 ARM intrinsic
- vld3_dup_s32 ARM intrinsic
- vld3_dup_s64 ARM intrinsic
- vld3_dup_s8 ARM intrinsic
- vld3_dup_u16 ARM intrinsic
- vld3_dup_u32 ARM intrinsic
- vld3_dup_u64 ARM intrinsic
- vld3_dup_u8 ARM intrinsic
- vld3_f16 ARM intrinsic
- vld3_f32 ARM intrinsic
- vld3_lane_f16 ARM intrinsic
- vld3_lane_f32 ARM intrinsic
- vld3_lane_p16 ARM intrinsic
- vld3_lane_p8 ARM intrinsic
- vld3_lane_s16 ARM intrinsic
- vld3_lane_s32 ARM intrinsic
- vld3_lane_s8 ARM intrinsic
- vld3_lane_u16 ARM intrinsic
- vld3_lane_u32 ARM intrinsic
- vld3_lane_u8 ARM intrinsic
- vld3_p16 ARM intrinsic
- vld3_p8 ARM intrinsic
- vld3_s16 ARM intrinsic
- vld3_s32 ARM intrinsic
- vld3_s64 ARM intrinsic
- vld3_s8 ARM intrinsic
- vld3_u16 ARM intrinsic
- vld3_u32 ARM intrinsic
- vld3_u64 ARM intrinsic
- vld3_u8 ARM intrinsic
- vld3q_f16 ARM intrinsic
- vld3q_f32 ARM intrinsic
- vld3q_lane_f16 ARM intrinsic
- vld3q_lane_f32 ARM intrinsic
- vld3q_lane_p16 ARM intrinsic
- vld3q_lane_s16 ARM intrinsic
- vld3q_lane_s32 ARM intrinsic
- vld3q_lane_u16 ARM intrinsic
- vld3q_lane_u32 ARM intrinsic
- vld3q_p16 ARM intrinsic
- vld3q_p8 ARM intrinsic
- vld3q_s16 ARM intrinsic
- vld3q_s32 ARM intrinsic
- vld3q_s8 ARM intrinsic
- vld3q_u16 ARM intrinsic
- vld3q_u32 ARM intrinsic
- vld3q_u8 ARM intrinsic
- vld4_dup_f16 ARM intrinsic
- vld4_dup_f32 ARM intrinsic
- vld4_dup_p16 ARM intrinsic
- vld4_dup_p8 ARM intrinsic
- vld4_dup_s16 ARM intrinsic
- vld4_dup_s32 ARM intrinsic
- vld4_dup_s64 ARM intrinsic
- vld4_dup_s8 ARM intrinsic
- vld4_dup_u16 ARM intrinsic
- vld4_dup_u32 ARM intrinsic
- vld4_dup_u64 ARM intrinsic
- vld4_dup_u8 ARM intrinsic
- vld4_f16 ARM intrinsic
- vld4_f32 ARM intrinsic
- vld4_lane_f16 ARM intrinsic
- vld4_lane_f32 ARM intrinsic
- vld4_lane_p16 ARM intrinsic
- vld4_lane_p8 ARM intrinsic
- vld4_lane_s16 ARM intrinsic
- vld4_lane_s32 ARM intrinsic
- vld4_lane_s8 ARM intrinsic
- vld4_lane_u16 ARM intrinsic
- vld4_lane_u32 ARM intrinsic
- vld4_lane_u8 ARM intrinsic
- vld4_p16 ARM intrinsic
- vld4_p8 ARM intrinsic
- vld4_s16 ARM intrinsic
- vld4_s32 ARM intrinsic
- vld4_s64 ARM intrinsic
- vld4_s8 ARM intrinsic
- vld4_u16 ARM intrinsic
- vld4_u32 ARM intrinsic
- vld4_u64 ARM intrinsic
- vld4_u8 ARM intrinsic
- vld4q_f16 ARM intrinsic
- vld4q_f32 ARM intrinsic
- vld4q_lane_f16 ARM intrinsic
- vld4q_lane_f32 ARM intrinsic
- vld4q_lane_p16 ARM intrinsic
- vld4q_lane_s16 ARM intrinsic
- vld4q_lane_s32 ARM intrinsic
- vld4q_lane_u16 ARM intrinsic
- vld4q_lane_u32 ARM intrinsic
- vld4q_p16 ARM intrinsic
- vld4q_p8 ARM intrinsic
- vld4q_s16 ARM intrinsic
- vld4q_s32 ARM intrinsic
- vld4q_s8 ARM intrinsic
- vld4q_u16 ARM intrinsic
- vld4q_u32 ARM intrinsic
- vld4q_u8 ARM intrinsic
- vmax_f32 ARM intrinsic
- vmax_s16 ARM intrinsic
- vmax_s32 ARM intrinsic
- vmax_s8 ARM intrinsic
- vmax_u16 ARM intrinsic
- vmax_u32 ARM intrinsic
- vmax_u8 ARM intrinsic
- vmaxq_f32 ARM intrinsic
- vmaxq_s16 ARM intrinsic
- vmaxq_s32 ARM intrinsic
- vmaxq_s8 ARM intrinsic
- vmaxq_u16 ARM intrinsic
- vmaxq_u32 ARM intrinsic
- vmaxq_u8 ARM intrinsic
- vmin_f32 ARM intrinsic
- vmin_s16 ARM intrinsic
- vmin_s32 ARM intrinsic
- vmin_s8 ARM intrinsic
- vmin_u16 ARM intrinsic
- vmin_u32 ARM intrinsic
- vmin_u8 ARM intrinsic
- vminq_f32 ARM intrinsic
- vminq_s16 ARM intrinsic
- vminq_s32 ARM intrinsic
- vminq_s8 ARM intrinsic
- vminq_u16 ARM intrinsic
- vminq_u32 ARM intrinsic
- vminq_u8 ARM intrinsic
- vmla_f32 ARM intrinsic
- vmla_lane_f32 ARM intrinsic
- vmla_lane_s16 ARM intrinsic
- vmla_lane_s32 ARM intrinsic
- vmla_lane_u16 ARM intrinsic
- vmla_lane_u32 ARM intrinsic
- vmla_n_f32 ARM intrinsic
- vmla_n_s16 ARM intrinsic
- vmla_n_s32 ARM intrinsic
- vmla_n_u16 ARM intrinsic
- vmla_n_u32 ARM intrinsic
- vmla_s16 ARM intrinsic
- vmla_s32 ARM intrinsic
- vmla_s8 ARM intrinsic
- vmla_u16 ARM intrinsic
- vmla_u32 ARM intrinsic
- vmla_u8 ARM intrinsic
- vmlal_lane_s16 ARM intrinsic
- vmlal_lane_s32 ARM intrinsic
- vmlal_lane_u16 ARM intrinsic
- vmlal_lane_u32 ARM intrinsic
- vmlal_n_s16 ARM intrinsic
- vmlal_n_s32 ARM intrinsic
- vmlal_n_u16 ARM intrinsic
- vmlal_n_u32 ARM intrinsic
- vmlal_s16 ARM intrinsic
- vmlal_s32 ARM intrinsic
- vmlal_s8 ARM intrinsic
- vmlal_u16 ARM intrinsic
- vmlal_u32 ARM intrinsic
- vmlal_u8 ARM intrinsic
- vmlaq_f32 ARM intrinsic
- vmlaq_lane_f32 ARM intrinsic
- vmlaq_lane_s16 ARM intrinsic
- vmlaq_lane_s32 ARM intrinsic
- vmlaq_lane_u16 ARM intrinsic
- vmlaq_lane_u32 ARM intrinsic
- vmlaq_n_f32 ARM intrinsic
- vmlaq_n_s16 ARM intrinsic
- vmlaq_n_s32 ARM intrinsic
- vmlaq_n_u16 ARM intrinsic
- vmlaq_n_u32 ARM intrinsic
- vmlaq_s16 ARM intrinsic
- vmlaq_s32 ARM intrinsic
- vmlaq_s8 ARM intrinsic
- vmlaq_u16 ARM intrinsic
- vmlaq_u32 ARM intrinsic
- vmlaq_u8 ARM intrinsic
- vmls_f32 ARM intrinsic
- vmls_lane_f32 ARM intrinsic
- vmls_lane_s16 ARM intrinsic
- vmls_lane_s32 ARM intrinsic
- vmls_lane_u16 ARM intrinsic
- vmls_lane_u32 ARM intrinsic
- vmls_n_f32 ARM intrinsic
- vmls_n_s16 ARM intrinsic
- vmls_n_s32 ARM intrinsic
- vmls_n_u16 ARM intrinsic
- vmls_n_u32 ARM intrinsic
- vmls_s16 ARM intrinsic
- vmls_s32 ARM intrinsic
- vmls_s8 ARM intrinsic
- vmls_u16 ARM intrinsic
- vmls_u32 ARM intrinsic
- vmls_u8 ARM intrinsic
- vmlsl_lane_s16 ARM intrinsic
- vmlsl_lane_s32 ARM intrinsic
- vmlsl_lane_u16 ARM intrinsic
- vmlsl_lane_u32 ARM intrinsic
- vmlsl_n_s16 ARM intrinsic
- vmlsl_n_s32 ARM intrinsic
- vmlsl_n_u16 ARM intrinsic
- vmlsl_n_u32 ARM intrinsic
- vmlsl_s16 ARM intrinsic
- vmlsl_s32 ARM intrinsic
- vmlsl_s8 ARM intrinsic
- vmlsl_u16 ARM intrinsic
- vmlsl_u32 ARM intrinsic
- vmlsl_u8 ARM intrinsic
- vmlsq_lane_f32 ARM intrinsic
- vmlsq_lane_s16 ARM intrinsic
- vmlsq_lane_s32 ARM intrinsic
- vmlsq_lane_u16 ARM intrinsic
- vmlsq_lane_u32 ARM intrinsic
- vmlsq_n_f32 ARM intrinsic
- vmlsq_n_s16 ARM intrinsic
- vmlsq_n_s32 ARM intrinsic
- vmlsq_n_u16 ARM intrinsic
- vmlsq_n_u32 ARM intrinsic
- vmlsq_s16 ARM intrinsic
- vmlsq_s32 ARM intrinsic
- vmlsq_s8 ARM intrinsic
- vmov_n_f32 ARM intrinsic
- vmov_n_p16 ARM intrinsic
- vmov_n_p8 ARM intrinsic
- vmov_n_s16 ARM intrinsic
- vmov_n_s32 ARM intrinsic
- vmov_n_s64 ARM intrinsic
- vmov_n_s8 ARM intrinsic
- vmov_n_u16 ARM intrinsic
- vmov_n_u32 ARM intrinsic
- vmov_n_u64 ARM intrinsic
- vmov_n_u8 ARM intrinsic
- vmovl_s16 ARM intrinsic
- vmovl_s32 ARM intrinsic
- vmovl_s8 ARM intrinsic
- vmovl_u16 ARM intrinsic
- vmovl_u32 ARM intrinsic
- vmovl_u8 ARM intrinsic
- vmovn_s16 ARM intrinsic
- vmovn_s32 ARM intrinsic
- vmovn_s64 ARM intrinsic
- vmovn_u16 ARM intrinsic
- vmovn_u32 ARM intrinsic
- vmovn_u64 ARM intrinsic
- vmovq_n_f32 ARM intrinsic
- vmovq_n_p16 ARM intrinsic
- vmovq_n_p8 ARM intrinsic
- vmovq_n_s16 ARM intrinsic
- vmovq_n_s32 ARM intrinsic
- vmovq_n_s64 ARM intrinsic
- vmovq_n_s8 ARM intrinsic
- vmovq_n_u16 ARM intrinsic
- vmovq_n_u32 ARM intrinsic
- vmovq_n_u64 ARM intrinsic
- vmovq_n_u8 ARM intrinsic
- vmul_f32 ARM intrinsic
- vmul_n_f32 ARM intrinsic
- vmul_n_s16 ARM intrinsic
- vmul_n_s32 ARM intrinsic
- vmul_n_u16 ARM intrinsic
- vmul_n_u32 ARM intrinsic
- vmul_p8 ARM intrinsic
- vmul_s16 ARM intrinsic
- vmul_s32 ARM intrinsic
- vmul_s8 ARM intrinsic
- vmul_u16 ARM intrinsic
- vmul_u32 ARM intrinsic
- vmul_u8 ARM intrinsic
- vmull_lane_s16 ARM intrinsic
- vmull_lane_s32 ARM intrinsic
- vmull_lane_u16 ARM intrinsic
- vmull_lane_u32 ARM intrinsic
- vmull_n_s16 ARM intrinsic
- vmull_n_s32 ARM intrinsic
- vmull_n_u16 ARM intrinsic
- vmull_n_u32 ARM intrinsic
- vmull_p8 ARM intrinsic
- vmull_s16 ARM intrinsic
- vmull_s32 ARM intrinsic
- vmull_s8 ARM intrinsic
- vmull_u16 ARM intrinsic
- vmull_u32 ARM intrinsic
- vmull_u8 ARM intrinsic
- vmulq_f32 ARM intrinsic
- vmulq_n_f32 ARM intrinsic
- vmulq_n_s16 ARM intrinsic
- vmulq_n_s32 ARM intrinsic
- vmulq_n_u16 ARM intrinsic
- vmulq_n_u32 ARM intrinsic
- vmulq_p8 ARM intrinsic
- vmulq_s16 ARM intrinsic
- vmulq_s32 ARM intrinsic
- vmulq_s8 ARM intrinsic
- vmulq_u16 ARM intrinsic
- vmulq_u32 ARM intrinsic
- vmulq_u8 ARM intrinsic
- vmvn_p8 ARM intrinsic
- vmvn_s16 ARM intrinsic
- vmvn_s32 ARM intrinsic
- vmvn_s8 ARM intrinsic
- vmvn_u16 ARM intrinsic
- vmvn_u32 ARM intrinsic
- vmvn_u8 ARM intrinsic
- vmvnq_p8 ARM intrinsic
- vmvnq_s16 ARM intrinsic
- vmvnq_s32 ARM intrinsic
- vmvnq_s8 ARM intrinsic
- vmvnq_u16 ARM intrinsic
- vmvnq_u32 ARM intrinsic
- vmvnq_u8 ARM intrinsic
- vneg_f32 ARM intrinsic
- vneg_s16 ARM intrinsic
- vneg_s32 ARM intrinsic
- vneg_s8 ARM intrinsic
- vnegq_f32 ARM intrinsic
- vnegq_s16 ARM intrinsic
- vnegq_s32 ARM intrinsic
- vnegq_s8 ARM intrinsic
- vorn_s16 ARM intrinsic
- vorn_s32 ARM intrinsic
- vorn_s64 ARM intrinsic
- vorn_s8 ARM intrinsic
- vorn_u16 ARM intrinsic
- vorn_u32 ARM intrinsic
- vorn_u64 ARM intrinsic
- vorn_u8 ARM intrinsic
- vornq_s16 ARM intrinsic
- vornq_s32 ARM intrinsic
- vornq_s64 ARM intrinsic
- vornq_s8 ARM intrinsic
- vornq_u16 ARM intrinsic
- vornq_u32 ARM intrinsic
- vornq_u64 ARM intrinsic
- vornq_u8 ARM intrinsic
- vorr_s16 ARM intrinsic
- vorr_s32 ARM intrinsic
- vorr_s64 ARM intrinsic
- vorr_s8 ARM intrinsic
- vorr_u16 ARM intrinsic
- vorr_u32 ARM intrinsic
- vorr_u64 ARM intrinsic
- vorr_u8 ARM intrinsic
- vorrq_s16 ARM intrinsic
- vorrq_s32 ARM intrinsic
- vorrq_s64 ARM intrinsic
- vorrq_s8 ARM intrinsic
- vorrq_u16 ARM intrinsic
- vorrq_u32 ARM intrinsic
- vorrq_u64 ARM intrinsic
- vorrq_u8 ARM intrinsic
- vpadal_s16 ARM intrinsic
- vpadal_s32 ARM intrinsic
- vpadal_s8 ARM intrinsic
- vpadal_u16 ARM intrinsic
- vpadal_u32 ARM intrinsic
- vpadal_u8 ARM intrinsic
- vpadalq_s16 ARM intrinsic
- vpadalq_s32 ARM intrinsic
- vpadalq_s8 ARM intrinsic
- vpadalq_u16 ARM intrinsic
- vpadalq_u32 ARM intrinsic
- vpadalq_u8 ARM intrinsic
- vpadd_f32 ARM intrinsic
- vpadd_s16 ARM intrinsic
- vpadd_s32 ARM intrinsic
- vpadd_s8 ARM intrinsic
- vpadd_u16 ARM intrinsic
- vpadd_u32 ARM intrinsic
- vpadd_u8 ARM intrinsic
- vpaddl_s16 ARM intrinsic
- vpaddl_s32 ARM intrinsic
- vpaddl_s8 ARM intrinsic
- vpaddl_u16 ARM intrinsic
- vpaddl_u32 ARM intrinsic
- vpaddl_u8 ARM intrinsic
- vpaddlq_s16 ARM intrinsic
- vpaddlq_s32 ARM intrinsic
- vpaddlq_s8 ARM intrinsic
- vpaddlq_u16 ARM intrinsic
- vpaddlq_u32 ARM intrinsic
- vpaddlq_u8 ARM intrinsic
- vpmax_f32 ARM intrinsic
- vpmax_s16 ARM intrinsic
- vpmax_s32 ARM intrinsic
- vpmax_s8 ARM intrinsic
- vpmax_u16 ARM intrinsic
- vpmax_u32 ARM intrinsic
- vpmax_u8 ARM intrinsic
- vpmin_f32 ARM intrinsic
- vpmin_s16 ARM intrinsic
- vpmin_s32 ARM intrinsic
- vpmin_s8 ARM intrinsic
- vpmin_u16 ARM intrinsic
- vpmin_u32 ARM intrinsic
- vpmin_u8 ARM intrinsic
- vqabs_s16 ARM intrinsic
- vqabs_s32 ARM intrinsic
- vqabs_s8 ARM intrinsic
- vqabsq_s16 ARM intrinsic
- vqabsq_s32 ARM intrinsic
- vqabsq_s8 ARM intrinsic
- vqadd_s16 ARM intrinsic
- vqadd_s32 ARM intrinsic
- vqadd_s64 ARM intrinsic
- vqadd_s8 ARM intrinsic
- vqadd_u16 ARM intrinsic
- vqadd_u32 ARM intrinsic
- vqadd_u64 ARM intrinsic
- vqadd_u8 ARM intrinsic
- vqaddq_s16 ARM intrinsic
- vqaddq_s32 ARM intrinsic
- vqaddq_s64 ARM intrinsic
- vqaddq_s8 ARM intrinsic
- vqaddq_u16 ARM intrinsic
- vqaddq_u32 ARM intrinsic
- vqaddq_u64 ARM intrinsic
- vqaddq_u8 ARM intrinsic
- vqdmlal_lane_s16 ARM intrinsic
- vqdmlal_lane_s32 ARM intrinsic
- vqdmlal_n_s16 ARM intrinsic
- vqdmlal_n_s32 ARM intrinsic
- vqdmlal_s16 ARM intrinsic
- vqdmlal_s32 ARM intrinsic
- vqdmlsl_lane_s16 ARM intrinsic
- vqdmlsl_lane_s32 ARM intrinsic
- vqdmlsl_n_s16 ARM intrinsic
- vqdmlsl_n_s32 ARM intrinsic
- vqdmlsl_s16 ARM intrinsic
- vqdmlsl_s32 ARM intrinsic
- vqdmulh_lane_s16 ARM intrinsic
- vqdmulh_lane_s32 ARM intrinsic
- vqdmulh_n_s16 ARM intrinsic
- vqdmulh_n_s32 ARM intrinsic
- vqdmulh_s16 ARM intrinsic
- vqdmulh_s32 ARM intrinsic
- vqdmulhq_lane_s16 ARM intrinsic
- vqdmulhq_lane_s32 ARM intrinsic
- vqdmulhq_n_s16 ARM intrinsic
- vqdmulhq_n_s32 ARM intrinsic
- vqdmulhq_s16 ARM intrinsic
- vqdmulhq_s32 ARM intrinsic
- vqdmull_lane_s16 ARM intrinsic
- vqdmull_lane_s32 ARM intrinsic
- vqdmull_n_s16 ARM intrinsic
- vqdmull_n_s32 ARM intrinsic
- vqdmull_s16 ARM intrinsic
- vqdmull_s32 ARM intrinsic
- vqmovn_s16 ARM intrinsic
- vqmovn_s32 ARM intrinsic
- vqmovn_s64 ARM intrinsic
- vqmovn_u16 ARM intrinsic
- vqmovn_u32 ARM intrinsic
- vqmovn_u64 ARM intrinsic
- vqmovun_s16 ARM intrinsic
- vqmovun_s32 ARM intrinsic
- vqmovun_s64 ARM intrinsic
- vqneg_s16 ARM intrinsic
- vqneg_s32 ARM intrinsic
- vqneg_s8 ARM intrinsic
- vqnegq_s16 ARM intrinsic
- vqnegq_s32 ARM intrinsic
- vqnegq_s8 ARM intrinsic
- vqrdmulh_lane_s16 ARM intrinsic
- vqrdmulh_lane_s32 ARM intrinsic
- vqrdmulh_n_s16 ARM intrinsic
- vqrdmulh_n_s32 ARM intrinsic
- vqrdmulh_s16 ARM intrinsic
- vqrdmulh_s32 ARM intrinsic
- vqrdmulhq_lane_s16 ARM intrinsic
- vqrdmulhq_lane_s32 ARM intrinsic
- vqrdmulhq_n_s16 ARM intrinsic
- vqrdmulhq_n_s32 ARM intrinsic
- vqrdmulhq_s16 ARM intrinsic
- vqrdmulhq_s32 ARM intrinsic
- vqrshl_s16 ARM intrinsic
- vqrshl_s32 ARM intrinsic
- vqrshl_s64 ARM intrinsic
- vqrshl_s8 ARM intrinsic
- vqrshl_u16 ARM intrinsic
- vqrshl_u32 ARM intrinsic
- vqrshl_u64 ARM intrinsic
- vqrshl_u8 ARM intrinsic
- vqrshlq_s16 ARM intrinsic
- vqrshlq_s32 ARM intrinsic
- vqrshlq_s64 ARM intrinsic
- vqrshlq_s8 ARM intrinsic
- vqrshlq_u16 ARM intrinsic
- vqrshlq_u32 ARM intrinsic
- vqrshlq_u64 ARM intrinsic
- vqrshlq_u8 ARM intrinsic
- vqrshrn_n_s16 ARM intrinsic
- vqrshrn_n_s32 ARM intrinsic
- vqrshrn_n_s64 ARM intrinsic
- vqrshrn_n_u16 ARM intrinsic
- vqrshrn_n_u32 ARM intrinsic
- vqrshrn_n_u64 ARM intrinsic
- vqrshrun_n_s16 ARM intrinsic
- vqrshrun_n_s32 ARM intrinsic
- vqrshrun_n_s64 ARM intrinsic
- vqshl_n_s16 ARM intrinsic
- vqshl_n_s32 ARM intrinsic
- vqshl_n_s64 ARM intrinsic
- vqshl_n_s8 ARM intrinsic
- vqshl_n_u16 ARM intrinsic
- vqshl_n_u32 ARM intrinsic
- vqshl_n_u64 ARM intrinsic
- vqshl_n_u8 ARM intrinsic
- vqshl_s16 ARM intrinsic
- vqshl_s32 ARM intrinsic
- vqshl_s64 ARM intrinsic
- vqshl_s8 ARM intrinsic
- vqshl_u16 ARM intrinsic
- vqshl_u32 ARM intrinsic
- vqshl_u64 ARM intrinsic
- vqshl_u8 ARM intrinsic
- vqshlq_n_s16 ARM intrinsic
- vqshlq_n_s32 ARM intrinsic
- vqshlq_n_s64 ARM intrinsic
- vqshlq_n_s8 ARM intrinsic
- vqshlq_n_u16 ARM intrinsic
- vqshlq_n_u32 ARM intrinsic
- vqshlq_n_u64 ARM intrinsic
- vqshlq_n_u8 ARM intrinsic
- vqshlq_s16 ARM intrinsic
- vqshlq_s32 ARM intrinsic
- vqshlq_s64 ARM intrinsic
- vqshlq_s8 ARM intrinsic
- vqshlq_u16 ARM intrinsic
- vqshlq_u32 ARM intrinsic
- vqshlq_u64 ARM intrinsic
- vqshlq_u8 ARM intrinsic
- vqshlu_n_s16 ARM intrinsic
- vqshlu_n_s32 ARM intrinsic
- vqshlu_n_s64 ARM intrinsic
- vqshlu_n_s8 ARM intrinsic
- vqshluq_n_s16 ARM intrinsic
- vqshluq_n_s32 ARM intrinsic
- vqshluq_n_s64 ARM intrinsic
- vqshluq_n_s8 ARM intrinsic
- vqshrn_n_s16 ARM intrinsic
- vqshrn_n_s32 ARM intrinsic
- vqshrn_n_s64 ARM intrinsic
- vqshrn_n_u16 ARM intrinsic
- vqshrn_n_u32 ARM intrinsic
- vqshrn_n_u64 ARM intrinsic
- vqshrun_n_s16 ARM intrinsic
- vqshrun_n_s32 ARM intrinsic
- vqshrun_n_s64 ARM intrinsic
- vqsub_s16 ARM intrinsic
- vqsub_s32 ARM intrinsic
- vqsub_s64 ARM intrinsic
- vqsub_s8 ARM intrinsic
- vqsub_u16 ARM intrinsic
- vqsub_u32 ARM intrinsic
- vqsub_u64 ARM intrinsic
- vqsub_u8 ARM intrinsic
- vqsubq_s16 ARM intrinsic
- vqsubq_s32 ARM intrinsic
- vqsubq_s64 ARM intrinsic
- vqsubq_s8 ARM intrinsic
- vqsubq_u16 ARM intrinsic
- vqsubq_u32 ARM intrinsic
- vqsubq_u64 ARM intrinsic
- vqsubq_u8 ARM intrinsic
- vraddhn_s16 ARM intrinsic
- vraddhn_s32 ARM intrinsic
- vraddhn_s64 ARM intrinsic
- vraddhn_u16 ARM intrinsic
- vraddhn_u32 ARM intrinsic
- vraddhn_u64 ARM intrinsic
- vrecpe_f32 ARM intrinsic
- vrecpe_u32 ARM intrinsic
- vrecpeq_f32 ARM intrinsic
- vrecpeq_u32 ARM intrinsic
- vrecps_f32 ARM intrinsic
- vrecpsq_f32 ARM intrinsic
- vrev16_p8 ARM intrinsic
- vrev16_s8 ARM intrinsic
- vrev16_u8 ARM intrinsic
- vrev16q_p8 ARM intrinsic
- vrev16q_s8 ARM intrinsic
- vrev16q_u8 ARM intrinsic
- vrev32_p8 ARM intrinsic
- vrev32_s16 ARM intrinsic
- vrev32_s8 ARM intrinsic
- vrev32_u16 ARM intrinsic
- vrev32_u8 ARM intrinsic
- vrev32q_p8 ARM intrinsic
- vrev32q_s16 ARM intrinsic
- vrev32q_s8 ARM intrinsic
- vrev32q_u16 ARM intrinsic
- vrev32q_u8 ARM intrinsic
- vrev64_f32 ARM intrinsic
- vrev64_p16 ARM intrinsic
- vrev64_p8 ARM intrinsic
- vrev64_s16 ARM intrinsic
- vrev64_s32 ARM intrinsic
- vrev64_s8 ARM intrinsic
- vrev64_u16 ARM intrinsic
- vrev64_u32 ARM intrinsic
- vrev64_u8 ARM intrinsic
- vrev64q_f32 ARM intrinsic
- vrev64q_p16 ARM intrinsic
- vrev64q_p8 ARM intrinsic
- vrev64q_s16 ARM intrinsic
- vrev64q_s32 ARM intrinsic
- vrev64q_s8 ARM intrinsic
- vrev64q_u16 ARM intrinsic
- vrev64q_u32 ARM intrinsic
- vrev64q_u8 ARM intrinsic
- vrhadd_s16 ARM intrinsic
- vrhadd_s32 ARM intrinsic
- vrhadd_s8 ARM intrinsic
- vrhadd_u16 ARM intrinsic
- vrhadd_u32 ARM intrinsic
- vrhadd_u8 ARM intrinsic
- vrhaddq_s16 ARM intrinsic
- vrhaddq_s32 ARM intrinsic
- vrhaddq_s8 ARM intrinsic
- vrhaddq_u16 ARM intrinsic
- vrhaddq_u32 ARM intrinsic
- vrhaddq_u8 ARM intrinsic
- vrshl_s16 ARM intrinsic
- vrshl_s32 ARM intrinsic
- vrshl_s64 ARM intrinsic
- vrshl_s8 ARM intrinsic
- vrshl_u16 ARM intrinsic
- vrshl_u32 ARM intrinsic
- vrshl_u64 ARM intrinsic
- vrshl_u8 ARM intrinsic
- vrshlq_s16 ARM intrinsic
- vrshlq_s32 ARM intrinsic
- vrshlq_s64 ARM intrinsic
- vrshlq_s8 ARM intrinsic
- vrshlq_u16 ARM intrinsic
- vrshlq_u32 ARM intrinsic
- vrshlq_u64 ARM intrinsic
- vrshlq_u8 ARM intrinsic
- vrshr_n_s16 ARM intrinsic
- vrshr_n_s32 ARM intrinsic
- vrshr_n_s64 ARM intrinsic
- vrshr_n_s8 ARM intrinsic
- vrshr_n_u16 ARM intrinsic
- vrshr_n_u32 ARM intrinsic
- vrshr_n_u64 ARM intrinsic
- vrshr_n_u8 ARM intrinsic
- vrshrn_n_s16 ARM intrinsic
- vrshrn_n_s32 ARM intrinsic
- vrshrn_n_s64 ARM intrinsic
- vrshrn_n_u16 ARM intrinsic
- vrshrn_n_u32 ARM intrinsic
- vrshrn_n_u64 ARM intrinsic
- vrshrq_n_s16 ARM intrinsic
- vrshrq_n_s32 ARM intrinsic
- vrshrq_n_s64 ARM intrinsic
- vrshrq_n_s8 ARM intrinsic
- vrshrq_n_u16 ARM intrinsic
- vrshrq_n_u32 ARM intrinsic
- vrshrq_n_u64 ARM intrinsic
- vrshrq_n_u8 ARM intrinsic
- vrsqrte_f32 ARM intrinsic
- vrsqrte_u32 ARM intrinsic
- vrsqrteq_f32 ARM intrinsic
- vrsqrteq_u32 ARM intrinsic
- vrsqrts_f32 ARM intrinsic
- vrsqrtsq_f32 ARM intrinsic
- vrsra_n_s16 ARM intrinsic
- vrsra_n_s32 ARM intrinsic
- vrsra_n_s64 ARM intrinsic
- vrsra_n_s8 ARM intrinsic
- vrsra_n_u16 ARM intrinsic
- vrsra_n_u32 ARM intrinsic
- vrsra_n_u64 ARM intrinsic
- vrsra_n_u8 ARM intrinsic
- vrsraq_n_s16 ARM intrinsic
- vrsraq_n_s32 ARM intrinsic
- vrsraq_n_s64 ARM intrinsic
- vrsraq_n_s8 ARM intrinsic
- vrsraq_n_u16 ARM intrinsic
- vrsraq_n_u32 ARM intrinsic
- vrsraq_n_u64 ARM intrinsic
- vrsraq_n_u8 ARM intrinsic
- vrsubhn_s16 ARM intrinsic
- vrsubhn_s32 ARM intrinsic
- vrsubhn_s64 ARM intrinsic
- vrsubhn_u16 ARM intrinsic
- vrsubhn_u32 ARM intrinsic
- vrsubhn_u64 ARM intrinsic
- vset_lane_f32 ARM intrinsic
- vset_lane_p16 ARM intrinsic
- vset_lane_p8 ARM intrinsic
- vset_lane_s16 ARM intrinsic
- vset_lane_s32 ARM intrinsic
- vset_lane_s64 ARM intrinsic
- vset_lane_s8 ARM intrinsic
- vset_lane_u16 ARM intrinsic
- vset_lane_u32 ARM intrinsic
- vset_lane_u64 ARM intrinsic
- vset_lane_u8 ARM intrinsic
- vsetq_lane_f32 ARM intrinsic
- vsetq_lane_p16 ARM intrinsic
- vsetq_lane_p8 ARM intrinsic
- vsetq_lane_s16 ARM intrinsic
- vsetq_lane_s32 ARM intrinsic
- vsetq_lane_s64 ARM intrinsic
- vsetq_lane_s8 ARM intrinsic
- vsetq_lane_u16 ARM intrinsic
- vsetq_lane_u32 ARM intrinsic
- vsetq_lane_u64 ARM intrinsic
- vsetq_lane_u8 ARM intrinsic
- vshl_n_s16 ARM intrinsic
- vshl_n_s32 ARM intrinsic
- vshl_n_s64 ARM intrinsic
- vshl_n_s8 ARM intrinsic
- vshl_n_u16 ARM intrinsic
- vshl_n_u32 ARM intrinsic
- vshl_n_u64 ARM intrinsic
- vshl_n_u8 ARM intrinsic
- vshl_s16 ARM intrinsic
- vshl_s32 ARM intrinsic
- vshl_s64 ARM intrinsic
- vshl_s8 ARM intrinsic
- vshl_u16 ARM intrinsic
- vshl_u32 ARM intrinsic
- vshl_u64 ARM intrinsic
- vshl_u8 ARM intrinsic
- vshll_n_s16 ARM intrinsic
- vshll_n_s32 ARM intrinsic
- vshll_n_s8 ARM intrinsic
- vshll_n_u16 ARM intrinsic
- vshll_n_u32 ARM intrinsic
- vshll_n_u8 ARM intrinsic
- vshlq_n_s16 ARM intrinsic
- vshlq_n_s32 ARM intrinsic
- vshlq_n_s64 ARM intrinsic
- vshlq_n_s8 ARM intrinsic
- vshlq_n_u16 ARM intrinsic
- vshlq_n_u32 ARM intrinsic
- vshlq_n_u64 ARM intrinsic
- vshlq_n_u8 ARM intrinsic
- vshlq_s16 ARM intrinsic
- vshlq_s32 ARM intrinsic
- vshlq_s64 ARM intrinsic
- vshlq_s8 ARM intrinsic
- vshlq_u16 ARM intrinsic
- vshlq_u32 ARM intrinsic
- vshlq_u64 ARM intrinsic
- vshlq_u8 ARM intrinsic
- vshr_n_s16 ARM intrinsic
- vshr_n_s32 ARM intrinsic
- vshr_n_s64 ARM intrinsic
- vshr_n_s8 ARM intrinsic
- vshr_n_u16 ARM intrinsic
- vshr_n_u32 ARM intrinsic
- vshr_n_u64 ARM intrinsic
- vshr_n_u8 ARM intrinsic
- vshrn_n_s16 ARM intrinsic
- vshrn_n_s32 ARM intrinsic
- vshrn_n_s64 ARM intrinsic
- vshrn_n_u16 ARM intrinsic
- vshrn_n_u32 ARM intrinsic
- vshrn_n_u64 ARM intrinsic
- vshrq_n_s16 ARM intrinsic
- vshrq_n_s32 ARM intrinsic
- vshrq_n_s64 ARM intrinsic
- vshrq_n_s8 ARM intrinsic
- vshrq_n_u16 ARM intrinsic
- vshrq_n_u32 ARM intrinsic
- vshrq_n_u64 ARM intrinsic
- vshrq_n_u8 ARM intrinsic
- vsli_n_p16 ARM intrinsic
- vsli_n_p8 ARM intrinsic
- vsli_n_s16 ARM intrinsic
- vsli_n_s32 ARM intrinsic
- vsli_n_s64 ARM intrinsic
- vsli_n_s8 ARM intrinsic
- vsli_n_u16 ARM intrinsic
- vsli_n_u32 ARM intrinsic
- vsli_n_u64 ARM intrinsic
- vsli_n_u8 ARM intrinsic
- vsliq_n_p16 ARM intrinsic
- vsliq_n_p8 ARM intrinsic
- vsliq_n_s16 ARM intrinsic
- vsliq_n_s32 ARM intrinsic
- vsliq_n_s64 ARM intrinsic
- vsliq_n_s8 ARM intrinsic
- vsliq_n_u16 ARM intrinsic
- vsliq_n_u32 ARM intrinsic
- vsliq_n_u64 ARM intrinsic
- vsliq_n_u8 ARM intrinsic
- vsra_n_s16 ARM intrinsic
- vsra_n_s32 ARM intrinsic
- vsra_n_s64 ARM intrinsic
- vsra_n_s8 ARM intrinsic
- vsra_n_u16 ARM intrinsic
- vsra_n_u32 ARM intrinsic
- vsra_n_u64 ARM intrinsic
- vsra_n_u8 ARM intrinsic
- vsraq_n_s16 ARM intrinsic
- vsraq_n_s32 ARM intrinsic
- vsraq_n_s64 ARM intrinsic
- vsraq_n_s8 ARM intrinsic
- vsraq_n_u16 ARM intrinsic
- vsraq_n_u32 ARM intrinsic
- vsraq_n_u64 ARM intrinsic
- vsraq_n_u8 ARM intrinsic
- vsri_n_p16 ARM intrinsic
- vsri_n_p8 ARM intrinsic
- vsri_n_s16 ARM intrinsic
- vsri_n_s32 ARM intrinsic
- vsri_n_s64 ARM intrinsic
- vsri_n_s8 ARM intrinsic
- vsri_n_u16 ARM intrinsic
- vsri_n_u32 ARM intrinsic
- vsri_n_u64 ARM intrinsic
- vsri_n_u8 ARM intrinsic
- vsriq_n_p16 ARM intrinsic
- vsriq_n_p8 ARM intrinsic
- vsriq_n_s16 ARM intrinsic
- vsriq_n_s32 ARM intrinsic
- vsriq_n_s64 ARM intrinsic
- vsriq_n_s8 ARM intrinsic
- vsriq_n_u16 ARM intrinsic
- vsriq_n_u32 ARM intrinsic
- vsriq_n_u64 ARM intrinsic
- vsriq_n_u8 ARM intrinsic
- vst1_f16 ARM intrinsic
- vst1_f32 ARM intrinsic
- vst1_lane_f16 ARM intrinsic
- vst1_lane_f32 ARM intrinsic
- vst1_lane_p16 ARM intrinsic
- vst1_lane_p8 ARM intrinsic
- vst1_lane_s16 ARM intrinsic
- vst1_lane_s32 ARM intrinsic
- vst1_lane_s64 ARM intrinsic
- vst1_lane_s8 ARM intrinsic
- vst1_lane_u16 ARM intrinsic
- vst1_lane_u32 ARM intrinsic
- vst1_lane_u64 ARM intrinsic
- vst1_lane_u8 ARM intrinsic
- vst1_p16 ARM intrinsic
- vst1_p8 ARM intrinsic
- vst1_s16 ARM intrinsic
- vst1_s32 ARM intrinsic
- vst1_s64 ARM intrinsic
- vst1_s8 ARM intrinsic
- vst1_u16 ARM intrinsic
- vst1_u32 ARM intrinsic
- vst1_u64 ARM intrinsic
- vst1_u8 ARM intrinsic
- vst1q_f16 ARM intrinsic
- vst1q_f32 ARM intrinsic
- vst1q_lane_f16 ARM intrinsic
- vst1q_lane_f32 ARM intrinsic
- vst1q_lane_p16 ARM intrinsic
- vst1q_lane_p8 ARM intrinsic
- vst1q_lane_s16 ARM intrinsic
- vst1q_lane_s32 ARM intrinsic
- vst1q_lane_s64 ARM intrinsic
- vst1q_lane_s8 ARM intrinsic
- vst1q_lane_u16 ARM intrinsic
- vst1q_lane_u32 ARM intrinsic
- vst1q_lane_u64 ARM intrinsic
- vst1q_lane_u8 ARM intrinsic
- vst1q_p16 ARM intrinsic
- vst1q_p8 ARM intrinsic
- vst1q_s16 ARM intrinsic
- vst1q_s32 ARM intrinsic
- vst1q_s64 ARM intrinsic
- vst1q_s8 ARM intrinsic
- vst1q_u16 ARM intrinsic
- vst1q_u32 ARM intrinsic
- vst1q_u64 ARM intrinsic
- vst1q_u8 ARM intrinsic
- vst2_f16 ARM intrinsic
- vst2_f32 ARM intrinsic
- vst2_lane_f16 ARM intrinsic
- vst2_lane_f32 ARM intrinsic
- vst2_lane_p16 ARM intrinsic
- vst2_lane_p8 ARM intrinsic
- vst2_lane_s16 ARM intrinsic
- vst2_lane_s32 ARM intrinsic
- vst2_lane_s8 ARM intrinsic
- vst2_lane_u16 ARM intrinsic
- vst2_lane_u32 ARM intrinsic
- vst2_lane_u8 ARM intrinsic
- vst2_p16 ARM intrinsic
- vst2_p8 ARM intrinsic
- vst2_s16 ARM intrinsic
- vst2_s32 ARM intrinsic
- vst2_s64 ARM intrinsic
- vst2_s8 ARM intrinsic
- vst2_u16 ARM intrinsic
- vst2_u32 ARM intrinsic
- vst2_u64 ARM intrinsic
- vst2_u8 ARM intrinsic
- vst2q_f16 ARM intrinsic
- vst2q_f32 ARM intrinsic
- vst2q_lane_f16 ARM intrinsic
- vst2q_lane_f32 ARM intrinsic
- vst2q_lane_p16 ARM intrinsic
- vst2q_lane_s16 ARM intrinsic
- vst2q_lane_s32 ARM intrinsic
- vst2q_lane_u16 ARM intrinsic
- vst2q_lane_u32 ARM intrinsic
- vst2q_p16 ARM intrinsic
- vst2q_p8 ARM intrinsic
- vst2q_s16 ARM intrinsic
- vst2q_s32 ARM intrinsic
- vst2q_s8 ARM intrinsic
- vst2q_u16 ARM intrinsic
- vst2q_u32 ARM intrinsic
- vst2q_u8 ARM intrinsic
- vst3_f16 ARM intrinsic
- vst3_f32 ARM intrinsic
- vst3_lane_f16 ARM intrinsic
- vst3_lane_f32 ARM intrinsic
- vst3_lane_p16 ARM intrinsic
- vst3_lane_p8 ARM intrinsic
- vst3_lane_s16 ARM intrinsic
- vst3_lane_s32 ARM intrinsic
- vst3_lane_s8 ARM intrinsic
- vst3_lane_u16 ARM intrinsic
- vst3_lane_u32 ARM intrinsic
- vst3_lane_u8 ARM intrinsic
- vst3_p16 ARM intrinsic
- vst3_p8 ARM intrinsic
- vst3_s16 ARM intrinsic
- vst3_s32 ARM intrinsic
- vst3_s64 ARM intrinsic
- vst3_s8 ARM intrinsic
- vst3_u16 ARM intrinsic
- vst3_u32 ARM intrinsic
- vst3_u64 ARM intrinsic
- vst3_u8 ARM intrinsic
- vst3q_f16 ARM intrinsic
- vst3q_f32 ARM intrinsic
- vst3q_lane_f16 ARM intrinsic
- vst3q_lane_f32 ARM intrinsic
- vst3q_lane_p16 ARM intrinsic
- vst3q_lane_s16 ARM intrinsic
- vst3q_lane_s32 ARM intrinsic
- vst3q_lane_u16 ARM intrinsic
- vst3q_lane_u32 ARM intrinsic
- vst3q_p16 ARM intrinsic
- vst3q_p8 ARM intrinsic
- vst3q_s16 ARM intrinsic
- vst3q_s32 ARM intrinsic
- vst3q_s8 ARM intrinsic
- vst3q_u16 ARM intrinsic
- vst3q_u32 ARM intrinsic
- vst3q_u8 ARM intrinsic
- vst4_f16 ARM intrinsic
- vst4_f32 ARM intrinsic
- vst4_lane_f16 ARM intrinsic
- vst4_lane_f32 ARM intrinsic
- vst4_lane_p16 ARM intrinsic
- vst4_lane_p8 ARM intrinsic
- vst4_lane_s16 ARM intrinsic
- vst4_lane_s32 ARM intrinsic
- vst4_lane_s8 ARM intrinsic
- vst4_lane_u16 ARM intrinsic
- vst4_lane_u32 ARM intrinsic
- vst4_lane_u8 ARM intrinsic
- vst4_p16 ARM intrinsic
- vst4_p8 ARM intrinsic
- vst4_s16 ARM intrinsic
- vst4_s32 ARM intrinsic
- vst4_s64 ARM intrinsic
- vst4_s8 ARM intrinsic
- vst4_u16 ARM intrinsic
- vst4_u32 ARM intrinsic
- vst4_u64 ARM intrinsic
- vst4_u8 ARM intrinsic
- vst4q_f16 ARM intrinsic
- vst4q_f32 ARM intrinsic
- vst4q_lane_f16 ARM intrinsic
- vst4q_lane_f32 ARM intrinsic
- vst4q_lane_p16 ARM intrinsic
- vst4q_lane_s16 ARM intrinsic
- vst4q_lane_s32 ARM intrinsic
- vst4q_lane_u16 ARM intrinsic
- vst4q_lane_u32 ARM intrinsic
- vst4q_p16 ARM intrinsic
- vst4q_p8 ARM intrinsic
- vst4q_s16 ARM intrinsic
- vst4q_s32 ARM intrinsic
- vst4q_s8 ARM intrinsic
- vst4q_u16 ARM intrinsic
- vst4q_u32 ARM intrinsic
- vst4q_u8 ARM intrinsic
- vsub_f32 ARM intrinsic
- vsub_s16 ARM intrinsic
- vsub_s32 ARM intrinsic
- vsub_s64 ARM intrinsic
- vsub_s8 ARM intrinsic
- vsub_u16 ARM intrinsic
- vsub_u32 ARM intrinsic
- vsub_u64 ARM intrinsic
- vsub_u8 ARM intrinsic
- vsubhn_s16 ARM intrinsic
- vsubhn_s32 ARM intrinsic
- vsubhn_s64 ARM intrinsic
- vsubhn_u16 ARM intrinsic
- vsubhn_u32 ARM intrinsic
- vsubhn_u64 ARM intrinsic
- vsubl_s16 ARM intrinsic
- vsubl_s32 ARM intrinsic
- vsubl_s8 ARM intrinsic
- vsubl_u16 ARM intrinsic
- vsubl_u32 ARM intrinsic
- vsubl_u8 ARM intrinsic
- vsubq_f32 ARM intrinsic
- vsubq_s16 ARM intrinsic
- vsubq_s32 ARM intrinsic
- vsubq_s64 ARM intrinsic
- vsubq_s8 ARM intrinsic
- vsubq_u16 ARM intrinsic
- vsubq_u32 ARM intrinsic
- vsubq_u64 ARM intrinsic
- vsubq_u8 ARM intrinsic
- vsubw_s16 ARM intrinsic
- vsubw_s32 ARM intrinsic
- vsubw_s8 ARM intrinsic
- vsubw_u16 ARM intrinsic
- vsubw_u32 ARM intrinsic
- vsubw_u8 ARM intrinsic
- vtbl1_p8 ARM intrinsic
- vtbl1_s8 ARM intrinsic
- vtbl1_u8 ARM intrinsic
- vtbl2_p8 ARM intrinsic
- vtbl2_s8 ARM intrinsic
- vtbl2_u8 ARM intrinsic
- vtbl3_p8 ARM intrinsic
- vtbl3_s8 ARM intrinsic
- vtbl3_u8 ARM intrinsic
- vtbl4_p8 ARM intrinsic
- vtbl4_s8 ARM intrinsic
- vtbl4_u8 ARM intrinsic
- vtbx1_p8 ARM intrinsic
- vtbx1_s8 ARM intrinsic
- vtbx1_u8 ARM intrinsic
- vtbx2_p8 ARM intrinsic
- vtbx2_s8 ARM intrinsic
- vtbx2_u8 ARM intrinsic
- vtbx3_p8 ARM intrinsic
- vtbx3_s8 ARM intrinsic
- vtbx3_u8 ARM intrinsic
- vtbx4_p8 ARM intrinsic
- vtbx4_s8 ARM intrinsic
- vtbx4_u8 ARM intrinsic
- vtrn_f32 ARM intrinsic
- vtrn_p16 ARM intrinsic
- vtrn_p8 ARM intrinsic
- vtrn_s16 ARM intrinsic
- vtrn_s32 ARM intrinsic
- vtrn_s8 ARM intrinsic
- vtrn_u16 ARM intrinsic
- vtrn_u32 ARM intrinsic
- vtrn_u8 ARM intrinsic
- vtrnq_f32 ARM intrinsic
- vtrnq_p16 ARM intrinsic
- vtrnq_p8 ARM intrinsic
- vtrnq_s16 ARM intrinsic
- vtrnq_s32 ARM intrinsic
- vtrnq_s8 ARM intrinsic
- vtrnq_u16 ARM intrinsic
- vtrnq_u32 ARM intrinsic
- vtrnq_u8 ARM intrinsic
- vtst_p8 ARM intrinsic
- vtst_s16 ARM intrinsic
- vtst_s32 ARM intrinsic
- vtst_s8 ARM intrinsic
- vtst_u16 ARM intrinsic
- vtst_u32 ARM intrinsic
- vtst_u8 ARM intrinsic
- vtstq_p8 ARM intrinsic
- vtstq_s16 ARM intrinsic
- vtstq_s32 ARM intrinsic
- vtstq_s8 ARM intrinsic
- vtstq_u16 ARM intrinsic
- vtstq_u32 ARM intrinsic
- vtstq_u8 ARM intrinsic
- vuzp_f32 ARM intrinsic
- vuzp_p16 ARM intrinsic
- vuzp_p8 ARM intrinsic
- vuzp_s16 ARM intrinsic
- vuzp_s32 ARM intrinsic
- vuzp_s8 ARM intrinsic
- vuzp_u16 ARM intrinsic
- vuzp_u32 ARM intrinsic
- vuzp_u8 ARM intrinsic
- vuzpq_f32 ARM intrinsic
- vuzpq_p16 ARM intrinsic
- vuzpq_p8 ARM intrinsic
- vuzpq_s16 ARM intrinsic
- vuzpq_s32 ARM intrinsic
- vuzpq_s8 ARM intrinsic
- vuzpq_u16 ARM intrinsic
- vuzpq_u32 ARM intrinsic
- vuzpq_u8 ARM intrinsic
- vzip_f32 ARM intrinsic
- vzip_p16 ARM intrinsic
- vzip_p8 ARM intrinsic
- vzip_s16 ARM intrinsic
- vzip_s8 ARM intrinsic
- vzip_u16 ARM intrinsic
- vzip_u8 ARM intrinsic
- vzipq_f32 ARM intrinsic
- vzipq_p16 ARM intrinsic
- vzipq_p8 ARM intrinsic
- vzipq_s16 ARM intrinsic
- vzipq_s32 ARM intrinsic
- vzipq_s8 ARM intrinsic
- vzipq_u16 ARM intrinsic
- vzipq_u32 ARM intrinsic
- vzipq_u8 ARM intrinsic
ms.assetid: d3d7dadd-7bd5-4508-8bff-371a66913e20
ms.openlocfilehash: 0b0ad779ad9d4c8de1623ea84dd6bc54e30703cc
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754490"
---
# <a name="arm-intrinsics"></a>ARM 内部函数

Microsoft C++编译器 （MSVC） 在 ARM 体系结构上提供了以下内部函数。 有关 ARM 的详细信息，请参阅[ARM 开发人员文档](https://developer.arm.com/docs)网站的体系结构和软件开发工具部分。

## <a name="neon"></a><a name="top"></a>霓虹灯

ARM 的 NEON 矢量指令集扩展提供单指令多数据 （SIMD） 功能，类似于 x86 和 x64 体系结构处理器常见的 MMX 和 SSE 矢量指令集中的功能。

根据头文件 `arm_neon.h`，霓虹灯内部函数受到支持。 对 NEON 内部函数的 MSVC 支持类似于 ARM 编译器的支持，该参数记录在 ARM 编译器工具链的附录 G[中，第 4.1 版在](https://go.microsoft.com/fwlink/p/?LinkId=251083)ARM 信息中心网站上的编译器参考中。

MSVC 和 ARM 编译器之间的主要区别是 MSVC 添加了`_ex``vldX`和`vstX`矢量加载和存储指令的变体。 `_ex` 变量采用附加参数，该参数指定指针参数的对齐情况但在其他方面与其非 `_ex` 对应项相同。

## <a name="arm-specific-intrinsics-listing"></a><a name="A"></a>特定于 ARM 的固有列表

|函数名称|指令|函数原型|
|-------------------|-----------------|------------------------|
|_arm_smlal|SMLAL|__int64_arm_smlal（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_umlal|UMLAL|未签名__int64_arm_umlal（无符号\__int64_RdHiLo，无符号_Rn，无符号int _Rm）|
|_arm_clz|CLZ|unsigned int _arm_clz(unsigned int _Rm)|
|_arm_qadd|QADD|int _arm_qadd(int _Rm, int _Rn)|
|_arm_qdadd|QDADD|int _arm_qdadd(int _Rm, int _Rn)|
|_arm_qdsub|QDSUB|int _arm_qdsub(int _Rm, int _Rn)|
|_arm_qsub|QSUB|int _arm_qsub(int _Rm, int _Rn)|
|_arm_smlabb|SMLABB|int _arm_smlabb(int _Rn, int _Rm, int _Ra)|
|_arm_smlabt|SMLABT|int _arm_smlabt(int _Rn, int _Rm, int _Ra)|
|_arm_smlatb|SMLATB|int _arm_smlatb(int _Rn, int _Rm, int _Ra)|
|_arm_smlatt|SMLATT|int _arm_smlatt(int _Rn, int _Rm, int _Ra)|
|_arm_smlalbb|SMLALBB|__int64_arm_smlalbb（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smlalbt|SMLALBT|__int64_arm_smlalbt（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smlaltb|SMLALTB|__int64_arm_smlaltb（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smlaltt|SMLALTT|__int64_arm_smlaltt（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smlawb|SMLAWB|int _arm_smlawb(int _Rn, int _Rm, int _Ra)|
|_arm_smlawt|SMLAWT|int _arm_smlawt(int _Rn, int _Rm, int _Ra)|
|_arm_smulbb|SMULBB|int _arm_smulbb(int _Rn, int _Rm)|
|_arm_smulbt|SMULBT|int _arm_smulbt(int _Rn, int _Rm)|
|_arm_smultb|SMULTB|int _arm_smultb(int _Rn, int _Rm)|
|_arm_smultt|SMULTT|int _arm_smultt(int _Rn, int _Rm)|
|_arm_smulwb|SMULWB|int _arm_smulwb(int _Rn, int _Rm)|
|_arm_smulwt|SMULWT|int _arm_smulwt(int _Rn, int _Rm)|
|_arm_sadd16|SADD16|int _arm_sadd16(int _Rn, int _Rm)|
|_arm_sadd8|SADD8|int _arm_sadd8(int _Rn, int _Rm)|
|_arm_sasx|SASX|int _arm_sasx(int _Rn, int _Rm)|
|_arm_ssax|SSAX|int _arm_ssax(int _Rn, int _Rm)|
|_arm_ssub16|SSUB16|int _arm_ssub16(int _Rn, int _Rm)|
|_arm_ssub8|SSUB8|int _arm_ssub8(int _Rn, int _Rm)|
|_arm_shadd16|SHADD16|int _arm_shadd16(int _Rn, int _Rm)|
|_arm_shadd8|SHADD8|int _arm_shadd8(int _Rn, int _Rm)|
|_arm_shasx|SHASX|int _arm_shasx(int _Rn, int _Rm)|
|_arm_shsax|SHSAX|int _arm_shsax(int _Rn, int _Rm)|
|_arm_shsub16|SHSUB16|int _arm_shsub16(int _Rn, int _Rm)|
|_arm_shsub8|SHSUB8|int _arm_shsub8(int _Rn, int _Rm)|
|_arm_qadd16|QADD16|int _arm_qadd16(int _Rn, int _Rm)|
|_arm_qadd8|QADD8|int _arm_qadd8(int _Rn, int _Rm)|
|_arm_qasx|QASX|int _arm_qasx(int _Rn, int _Rm)|
|_arm_qsax|QSAX|int _arm_qsax(int _Rn, int _Rm)|
|_arm_qsub16|QSUB16|int _arm_qsub16(int _Rn, int _Rm)|
|_arm_qsub8|QSUB8|int _arm_qsub8(int _Rn, int _Rm)|
|_arm_uadd16|UADD16|unsigned int _arm_uadd16(unsigned int _Rn, unsigned int _Rm)|
|_arm_uadd8|UADD8|unsigned int _arm_uadd8(unsigned int _Rn, unsigned int _Rm)|
|_arm_uasx|UASX|unsigned int _arm_uasx(unsigned int _Rn, unsigned int _Rm)|
|_arm_usax|USAX|unsigned int _arm_usax(unsigned int _Rn, unsigned int _Rm)|
|_arm_usub16|USUB16|unsigned int _arm_usub16(unsigned int _Rn, unsigned int _Rm)|
|_arm_usub8|USUB8|unsigned int _arm_usub8(unsigned int _Rn, unsigned int _Rm)|
|_arm_uhadd16|UHADD16|unsigned int _arm_uhadd16(unsigned int _Rn, unsigned int _Rm)|
|_arm_uhadd8|UHADD8|unsigned int _arm_uhadd8(unsigned int _Rn, unsigned int _Rm)|
|_arm_uhasx|UHASX|unsigned int _arm_uhasx(unsigned int _Rn, unsigned int _Rm)|
|_arm_uhsax|UHSAX|unsigned int _arm_uhsax(unsigned int _Rn, unsigned int _Rm)|
|_arm_uhsub16|UHSUB16|unsigned int _arm_uhsub16(unsigned int _Rn, unsigned int _Rm)|
|_arm_uhsub8|UHSUB8|unsigned int _arm_uhsub8(unsigned int _Rn, unsigned int _Rm)|
|_arm_uqadd16|UQADD16|unsigned int _arm_uqadd16(unsigned int _Rn, unsigned int _Rm)|
|_arm_uqadd8|UQADD8|unsigned int _arm_uqadd8(unsigned int _Rn, unsigned int _Rm)|
|_arm_uqasx|UQASX|unsigned int _arm_uqasx(unsigned int _Rn, unsigned int _Rm)|
|_arm_uqsax|UQSAX|unsigned int _arm_uqsax(unsigned int _Rn, unsigned int _Rm)|
|_arm_uqsub16|UQSUB16|unsigned int _arm_uqsub16(unsigned int _Rn, unsigned int _Rm)|
|_arm_uqsub8|UQSUB8|unsigned int _arm_uqsub8(unsigned int _Rn, unsigned int _Rm)|
|_arm_sxtab|SXTAB|int _arm_sxtab(int _Rn, int _Rm, unsigned int _Rotation)|
|_arm_sxtab16|SXTAB16|int _arm_sxtab16(int _Rn, int _Rm, unsigned int _Rotation)|
|_arm_sxtah|SXTAH|int _arm_sxtah(int _Rn, int _Rm, unsigned int _Rotation)|
|_arm_uxtab|UXTAB|unsigned int _arm_uxtab(unsigned int _Rn, unsigned int _Rm, unsigned int _Rotation)|
|_arm_uxtab16|UXTAB16|unsigned int _arm_uxta16b(unsigned int _Rn, unsigned int _Rm, unsigned int _Rotation)|
|_arm_uxtah|UXTAH|unsigned int _arm_uxtah(unsigned int _Rn, unsigned int _Rm, unsigned int _Rotation)|
|_arm_sxtb|SXTB|int _arm_sxtb(int _Rn, unsigned int _Rotation)|
|_arm_sxtb16|SXTB16|int _arm_sxtb16(int _Rn, unsigned int _Rotation)|
|_arm_sxth|SXTH|int _arm_sxth(int _Rn, unsigned int _Rotation)|
|_arm_uxtb|UXTB|unsigned int _arm_uxtb(unsigned int _Rn, unsigned int _Rotation)|
|_arm_uxtb16|UXTB16|unsigned int _arm_uxtb16(unsigned int _Rn, unsigned int _Rotation)|
|_arm_uxth|UXTH|unsigned int _arm_uxth(unsigned int _Rn, unsigned int _Rotation)|
|_arm_pkhbt|PKHBT|int _arm_pkhbt(int _Rn, int _Rm, unsigned int _Lsl_imm)|
|_arm_pkhtb|PKHTB|int _arm_pkhtb(int _Rn, int _Rm, unsigned int _Asr_imm)|
|_arm_usad8|USAD8|unsigned int _arm_usad8(unsigned int _Rn, unsigned int _Rm)|
|_arm_usada8|USADA8|unsigned int _arm_usada8(unsigned int _Rn, unsigned int _Rm, unsigned int _Ra)|
|_arm_ssat|SSAT|int _arm_ssat(unsigned int _Sat_imm, _int _Rn, _ARMINTR_SHIFT_T _Shift_type, unsigned int _Shift_imm)|
|_arm_usat|USAT|int _arm_usat(unsigned int _Sat_imm, _int _Rn, _ARMINTR_SHIFT_T _Shift_type, unsigned int _Shift_imm)|
|_arm_ssat16|SSAT16|int _arm_ssat16(unsigned int _Sat_imm, _int _Rn)|
|_arm_usat16|USAT16|int _arm_usat16(unsigned int _Sat_imm, _int _Rn)|
|_arm_rev|REV|unsigned int _arm_rev(unsigned int _Rm)|
|_arm_rev16|REV16|unsigned int _arm_rev16(unsigned int _Rm)|
|_arm_revsh|REVSH|unsigned int _arm_revsh(unsigned int _Rm)|
|_arm_smlad|SMLAD|int _arm_smlad(int _Rn, int _Rm, int _Ra)|
|_arm_smladx|SMLADX|int _arm_smladx(int _Rn, int _Rm, int _Ra)|
|_arm_smlsd|SMLSD|int _arm_smlsd(int _Rn, int _Rm, int _Ra)|
|_arm_smlsdx|SMLSDX|int _arm_smlsdx(int _Rn, int _Rm, int _Ra)|
|_arm_smmla|SMMLA|int _arm_smmla(int _Rn, int _Rm, int _Ra)|
|_arm_smmlar|SMMLAR|int _arm_smmlar(int _Rn, int _Rm, int _Ra)|
|_arm_smmls|SMMLS|int _arm_smmls(int _Rn, int _Rm, int _Ra)|
|_arm_smmlsr|SMMLSR|int _arm_smmlsr(int _Rn, int _Rm, int _Ra)|
|_arm_smmul|SMMUL|int _arm_smmul(int _Rn, int _Rm)|
|_arm_smmulr|SMMULR|int _arm_smmulr(int _Rn, int _Rm)|
|_arm_smlald|SMLALD|__int64_arm_smlald（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smlaldx|SMLALDX|__int64_arm_smlaldx（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smlsld|SMLSLD|__int64_arm_smlsld（_int64_RdHiLo，_Rn，_Rm）\_|
|_arm_smlsldx|SMLSLDX|__int64_arm_smlsldx（_int64_RdHiLo、_Rn、_Rm）\_|
|_arm_smuad|SMUAD|int _arm_smuad(int _Rn, int _Rm)|
|_arm_smuadx|SMUADX|int _arm_muadxs(int _Rn, int _Rm)|
|_arm_smusd|SMUSD|int _arm_smusd(int _Rn, int _Rm)|
|_arm_smusdx|SMUSDX|int _arm_smusdx(int _Rn, int _Rm)|
|_arm_smull|SMULL|__int64 _arm_smull(int _Rn, int _Rm)|
|_arm_umull|UMULL|unsigned __int64 _arm_umull(unsigned int _Rn, unsigned int _Rm)|
|_arm_umaal|UMAAL|unsigned __int64 _arm_umaal(unsigned int _RdLo, unsigned int _RdHi, unsigned int _Rn, unsigned int _Rm)|
|_arm_bfc|BFC|unsigned int _arm_bfc(unsigned int _Rd, unsigned int _Lsb, unsigned int _Width)|
|_arm_bfi|BFI|unsigned int _arm_bfi(unsigned int _Rd, unsigned int _Rn, unsigned int _Lsb, unsigned int _Width)|
|_arm_rbit|RBIT|unsigned int _arm_rbit(unsigned int _Rm)|
|_arm_sbfx|SBFX|int _arm_sbfx(int _Rn, unsigned int _Lsb, unsigned int _Width)|
|_arm_ubfx|UBFX|unsigned int _arm_ubfx(unsigned int _Rn, unsigned int _Lsb, unsigned int _Width)|
|_arm_sdiv|SDIV|int _arm_sdiv(int _Rn, int _Rm)|
|_arm_udiv|UDIV|unsigned int _arm_udiv(unsigned int _Rn, unsigned int _Rm)|
|__cps|CPS|void __cps(unsigned int _Ops, unsigned int _Flags, unsigned int _Mode)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关可强制执行的限制类型的详细信息，请参阅[内存障碍限制](#BarrierRestrictions)。|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关可强制执行的限制类型的详细信息，请参阅[内存障碍限制](#BarrierRestrictions)。|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关可强制执行的限制类型的详细信息，请参阅[内存障碍限制](#BarrierRestrictions)。|
|__emit||空__emit（无符号\__int32操作码）<br /><br /> 将指定指令插入由编译器输出的指令流中。<br /><br /> `opcode` 的值必须是在编译时已知的常量表达式。 指令字大小为 16 位且忽略 `opcode` 最重要的 16 位。<br /><br /> 在执行插入的指令之前，编译器不会尝试解释`opcode`的内容，也不保证 CPU 或内存状态。<br /><br /> 编译器假定 CPU 和内存状态在执行插入的指令后保持不变。 因此，更改状态的说明可能会对编译器生成的普通代码产生不利影响。<br /><br /> 因此，仅用于`emit`插入影响 CPU 状态的指令，编译器通常不会处理这些指令（例如，协处理器状态）或实现使用`declspec(naked)`声明的函数。|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__iso_volatile_load16||__int16_iso_volatile_load16（\_波动\__int16） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_load32||__int32_iso_volatile_load32（\_波动\__int32） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_load64||__int64_iso_volatile_load64（\_波动\__int64） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_load8||__int8_iso_volatile_load8（\_波动\__int8） \*<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store16||空__iso_volatile_store16（易\_挥\*_int16，_int16） \_<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store32||空__iso_volatile_store32（易\_\*挥_int32_int32） \_<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store64||空__iso_volatile_store64（易\_\*挥_int64，_int64） \_<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__iso_volatile_store8||空__iso_volatile_store8（挥\_发\*性\__int8，_int8）<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/存储内部函数](#IsoVolatileLoadStore)。|
|__ldrexd|LDREXD|__int64_ldrexd（\_波动_int64） \_ \*|
|__prefetch|PLD|_prefetch__cdecl\_空（空白\*）<br /><br /> 为系统提供一个 `PLD` 内存提示，便可很快访问指定地址处或指定地址附近的内存。 某些系统可能会选择优化此内存访问模式以提高运行时性能。 但是，从 c + + 语言的角度来看，此功能没有明显的影响，可能不执行任何操作。|
|__rdpmccntr64||未签名__int64_rdpmccntr64（\_无效）|
|__sev|SEV|void __sev(void)|
|__static_assert||空__static_assert（int，const \*char）|
|__swi|SVC|unsigned int __swi(unsigned int, ...)|
|__trap|BKPT|int __trap(int, ...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|_AddSatInt|QADD|int _AddSatInt(int, int)|
|_CopyDoubleFromInt64||双_CopyDoubleFromInt64（_int64）\_|
|_CopyFloatFromInt32||浮_CopyFloatFromInt32（_int32）\_|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||无符号_CountLeadingOnes64（无符号\__int64）|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||无符号_CountLeadingSigns64（_int64）\_|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||无符号的int_CountLeadingZeros64（无\_符号_int64）|
|_CountOneBits||unsigned int _CountOneBits(unsigned long)|
|_CountOneBits64||无符号的int_CountOneBits64（无\_符号_int64）|
|_DAddSatInt|QDADD|int _DAddSatInt(int, int)|
|_DSubSatInt|QDSUB|int _DSubSatInt(int, int)|
|_isunordered||int _isunordered(double, double)|
|_isunorderedf||int _isunorderedf(float, float)|
|_MoveFromCoprocessor|MRC|unsigned int _MoveFromCoprocessor(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息，请参阅[_MoveFromCoprocessor，_MoveFromCoprocessor2](#MoveFromCo)。|
|_MoveFromCoprocessor2|MRC2|unsigned int _MoveFromCoprocessor2(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息，请参阅[_MoveFromCoprocessor，_MoveFromCoprocessor2](#MoveFromCo)。|
|_MoveFromCoprocessor64|MRRC|unsigned __int64 _MoveFromCoprocessor64(unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息，请参阅[_MoveFromCoprocessor64](#MoveFromCo64)。|
|_MoveToCoprocessor|MCR|void _MoveToCoprocessor(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息，请参阅[_MoveToCoprocessor，_MoveToCoprocessor2](#MoveToCo)。|
|_MoveToCoprocessor2|MCR2|void _MoveToCoprocessor2(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息，请参阅[_MoveToCoprocessor，_MoveToCoprocessor2](#MoveToCo)。|
|_MoveToCoprocessor64|MCRR|无效_MoveToCoprocessor64（无符号\__int64、无符号 int、无符号 int、无符号 int）<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息，请参阅[_MoveToCoprocessor64](#MoveToCo64)。|
|_MulHigh||long _MulHigh(long, long)|
|_MulUnsignedHigh||unsigned long _MulUnsignedHigh(unsigned long, unsigned long)|
|_ReadBankedReg|MRS|int _ReadBankedReg(int _Reg)|
|_ReadStatusReg|MRS|int _ReadStatusReg(int)|
|_SubSatInt|QSUB|int _SubSatInt(int, int)|
|_WriteBankedReg|MSR|void _WriteBankedReg(int _Value, int _Reg)|
|_WriteStatusReg|MSR|void _WriteStatusReg(int, int, int)|

[[返回顶部](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>内存障碍限制

内部函数`__dmb`（数据内存屏障）、（`__dsb`数据同步屏障）和`__isb`（指令同步障碍）使用以下预定义值在共享域和受操作影响的访问类型方面指定内存障碍限制。

|限制值|说明|
|-----------------------|-----------------|
|_ARM_BARRIER_SY|完整系统，读取和写入操作。|
|_ARM_BARRIER_ST|完整系统，只写操作。|
|_ARM_BARRIER_ISH|内部可共享，读取和写入操作。|
|_ARM_BARRIER_ISHST|内部可共享，只写操作。|
|_ARM_BARRIER_NSH|不可共享，读取和写入操作。|
|_ARM_BARRIER_NSHST|不可共享，只写操作。|
|_ARM_BARRIER_OSH|外部可共享，读取和写入操作。|
|_ARM_BARRIER_OSHST|外部可共享，只写操作。|

对于 `__isb` 内部函数，当前有效的唯一限制是 _ARM_BARRIER_SY；其他所有值由体系结构进行保留。

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/存储内部

这些内部函数显式执行不受编译器优化约束的负载和存储。

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>参数

*位置*\
要从中读取或为其写入的内存位置的地址。

*价值*\
要写入指定内存位置的值（仅存储内部函数）。

#### <a name="return-value-load-intrinsics-only"></a>返回值（仅加载内部函数）

由 `Location` 指定的内存位置的值。

#### <a name="remarks"></a>备注

可以使用 和`__iso_volatile_load8/16/32/64``__iso_volatile_store8/16/32/64`内部函数显式执行不受编译器优化约束的内存访问。 编译器无法删除、合成或更改这些操作的相对顺序，但不会生成隐式硬件内存障碍。 因此，硬件仍可能对跨多个线程的可观察内存访问进行重新排序。 更确切地说，这些内在函数等效于以下表达式，这些表达式在 **/volatile：iso**下编译。

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

请注意内部函数采用易失性指针来适应易失性变量。 但是，没有要求或建议使用易失性指针作为参数。 如果使用常规非易失性类型，则这些操作的语义完全相同。

有关 **/volatile：iso**命令行参数的详细信息，请参阅[/volatile（易失性关键字解释）。](../build/reference/volatile-volatile-keyword-interpretation.md)

### <a name="_movefromcoprocessor-_movefromcoprocessor2"></a><a name="MoveFromCo"></a>_MoveFromCoprocessor2_MoveFromCoprocessor

这些内部函数通过使用协处理器数据传输指令从 ARM 协处理器读取数据。

```C
int _MoveFromCoprocessor(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);

int _MoveFromCoprocessor2(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);
```

#### <a name="parameters"></a>参数

*科多罗克*\
0 到 15 之间的协处理器编号。

*opcode1*\
0 到 7 之间特定于协处理器的操作码

*克恩*\
协处理器寄存器编号，在 0 到 15 之间，用于向指令指定第一个操作数。

*Crm*\
协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。

*opcode2*\
0 到 7 之间特定于附加协处理器的操作码。

#### <a name="return-value"></a>返回值

从协处理器中读取的值。

#### <a name="remarks"></a>备注

内部所有五个参数的值必须是编译时已知的常量表达式。

`_MoveFromCoprocessor` 使用 MRC 指令；`_MoveFromCoprocessor2` 使用 MRC2。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。

### <a name="_movefromcoprocessor64"></a><a name="MoveFromCo64"></a>_MoveFromCoprocessor64

使用协处理器数据传输指令，读取 ARM 协处理器中的数据。

```C
unsigned __int64 _MoveFromCoprocessor64(
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crm,
);
```

#### <a name="parameters"></a>参数

*科多罗克*\
0 到 15 之间的协处理器编号。

*opcode1*\
0 到 15 之间特定于协处理器的操作码。

*Crm*\
协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。

#### <a name="return-value"></a>返回值

从协处理器中读取的值。

#### <a name="remarks"></a>备注

内部所有三个参数的值必须是编译时已知的常量表达式。

`_MoveFromCoprocessor64` 使用 MRRC 指令。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。

### <a name="_movetocoprocessor-_movetocoprocessor2"></a><a name="MoveToCo"></a>_MoveToCoprocessor，_MoveToCoprocessor2

这些内部函数通过使用协处理器数据传输指令将数据写入到 ARM 协处理器。

```C
void _MoveToCoprocessor(
      unsigned int value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);

void _MoveToCoprocessor2(
      unsigned int value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crn,
      unsigned int crm,
      unsigned int opcode2
);
```

#### <a name="parameters"></a>参数

*价值*\
要写入到协处理器的值。

*科多罗克*\
0 到 15 之间的协处理器编号。

*opcode1*\
0 到 7 之间特定于协处理器的操作码。

*克恩*\
协处理器寄存器编号，在 0 到 15 之间，用于向指令指定第一个操作数。

*Crm*\
协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。

*opcode2*\
0 到 7 之间特定于附加协处理器的操作码。

#### <a name="return-value"></a>返回值

无。

#### <a name="remarks"></a>备注

`coproc``opcode1`内部值的值必须`opcode2`为编译时已知的常量表达式。 `crn` `crm`

`_MoveToCoprocessor` 使用 MCR 指令；`_MoveToCoprocessor2` 使用 MCR2。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。

### <a name="_movetocoprocessor64"></a><a name="MoveToCo64"></a>_MoveToCoprocessor64

这些内部函数通过使用协处理器数据传输指令将数据写入到 ARM 协处理器。

```C
void _MoveFromCoprocessor64(
      unsigned __int64 value,
      unsigned int coproc,
      unsigned int opcode1,
      unsigned int crm,
);
```

#### <a name="parameters"></a>参数

*科多罗克*\
0 到 15 之间的协处理器编号。

*opcode1*\
0 到 15 之间特定于协处理器的操作码。

*Crm*\
协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。

#### <a name="return-value"></a>返回值

无。

#### <a name="remarks"></a>备注

内部值和`coproc``crm`内部项`opcode1`的参数的值必须是编译时已知的常量表达式。

`_MoveFromCoprocessor64` 使用 MCRR 指令。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。

## <a name="arm-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM 支持其他体系结构的固有产品

下表列出了来自在 ARM 平台上受支持的其他体系结构的内部函数。 如果 ARM 上的内部函数行为不同于它在其他硬件体系结构上的行为，则记录其他详细信息。

|函数名称|函数原型|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|空__code_seg（康斯特字符\*）|
|__debugbreak|无效__cdecl_debugbreak（\_空）|
|__fastfail|__declspec（无返回）无效\__fastfail（无符号int）|
|__nop|无效__nop（无效）**注意：** 在 ARM 平台上，如果在目标体系结构中实现，此功能将生成 NOP 指令;否则，将生成不更改程序或 CPU 状态的替代指令，例如`MOV r8, r8`。 它在功能上等效于其他硬件体系结构\_的_nop内部。 由于目标体系结构可能会忽略对程序或 CPU 状态没有影响的指令作为优化，因此该指令不一定会消耗 CPU 周期。 因此，\_不要使用_nop内在操作代码序列的执行时间，除非您确定 CPU 的行为方式。 相反，\_您可以使用_nop内部函数将下一个指令与特定的 32 位边界地址对齐。|
|__yield|无效__yield（void）**注意：** 在 ARM 平台上，此函数生成 YIELD 指令，指示线程正在执行一个可以暂时暂停执行的任务（例如，旋转锁），而不会对程序产生负面影响。 它使 CPU 能够在执行周期内执行其他任务，否则这些任务会浪费。|
|_AddressOfReturnAddress|空\*_AddressOfReturnAddress（空）|
|_BitScanForward|无符号字符_BitScanForward（未签名的长\*_Index，未签名长_Mask）|
|_BitScanReverse|无符号字符_BitScanReverse（无符号长\*_Index，无符号长_Mask）|
|_bittest|无符号字符_bittest（长孔\*，长）|
|_bittestandcomplement|无符号字符_bittestandcomplement（长\*，长）|
|_bittestandreset|无符号字符_bittestandreset（长\*，长）|
|_bittestandset|无符号字符_bittestandset（长\*，长）|
|_byteswap_uint64|未签名__int64_cdecl_byteswap_uint64（\_未签名\__int64）|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|无效__cdecl_disable（无效）**注意：** 在 ARM 平台上，此功能生成 CPSID 指令;它只能作为一种内在的。|
|_enable|无效__cdecl_enable（无效）**注意：** 在 ARM 平台上，此功能生成 CPSIE 指令;它只能作为一种内在的。|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|空\*_ReturnAddress（空）|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|未签名__int64_cdecl_rotl64（\_未签名\__int64_Value，_Shift）|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|未签名__int64_cdecl_rotr64（\_未签名\__int64_Value，_Shift）|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[返回顶部](#top)]

## <a name="interlocked-intrinsics"></a>互锁内部

互锁内部函数是用于执行原子读取-修改-写入操作的一组内部函数。 其中一些互锁内部函数通用于所有平台。 它们在此处单独列出，因为其中有大量，但由于它们的定义大多是冗余的，因此更容易从一般角度考虑它们。 它们的名称可用于派生确切行为。

下表总结了非 bittest 互锁内部函数的 ARM 支持。 表中的每个单元格都对应一个名称，这些名称的派生方式是将该行的最左侧单元格中的操作名和该列的最上面单元格中的类型名附加到 `_Interlocked`。 例如，`Xor`行和`8`列交集处的单元格对应于`_InterlockedXor8`并完全支持。 大部分受支持的函数提供以下可选后缀：`_acq`、`_rel` 和 `_nf`。 `_acq` 后缀表示“获取”语义，而 `_rel` 后缀表示“发布”语义。 或`_nf`"无栅栏"后缀对 ARM 是唯一的，在下一节中将对此进行讨论。

||8|16|32|64|P|
|-|-------|--------|--------|--------|-------|
|添加|无|无|完全|完全|无|
|And|完全|完全|完全|完全|无|
|CompareExchange|完全|完全|完全|完全|完全|
|递减|无|完全|完全|完全|无|
|Exchange|部分|部分|部分|部分|部分|
|ExchangeAdd|完全|完全|完全|完全|无|
|增量|无|完全|完全|完全|无|
|Or|完全|完全|完全|完全|无|
|Xor|完全|完全|完全|完全|无|

注册表项：

- **完整**： 支持`_acq`普通`_rel`、、和`_nf`窗体。

- **部分**：支持普通`_acq`、`_nf`和 窗体。

- **无**： 不支持

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf（无栅栏）后缀

或`_nf`"无栅栏"后缀表示操作不作为任何类型的内存屏障，与其他三种形式（普通、`_acq`和`_rel`）不同，它们都作为某种屏障运行。 `_nf`窗体的一个可能用途是维护一个统计计数器，该计数器同时由多个线程更新，但在多个线程执行时，其值未以其他方式使用。

### <a name="list-of-interlocked-intrinsics"></a>互锁内部函数列表

|函数名称|函数原型|
|-------------------|------------------------|
|_InterlockedAdd|长_InterlockedAdd（长_volatile\*长）|
|_InterlockedAdd64|__int64_InterlockedAdd64（_int64\_波动\*，_int64） \_|
|_InterlockedAdd64_acq|__int64_InterlockedAdd64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedAdd64_nf|__int64_InterlockedAdd64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedAdd64_rel|__int64_InterlockedAdd64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedAdd_acq|长_InterlockedAdd_acq（长时间挥\*发性，长）|
|_InterlockedAdd_nf|长_InterlockedAdd_nf（长时间挥\*发性，长）|
|_InterlockedAdd_rel|长_InterlockedAdd_rel（长时间挥\*发性，长）|
|_InterlockedAnd|长_InterlockedAnd（长时间挥\*发性，长）|
|_InterlockedAnd16|短_InterlockedAnd16（短波动\*、短）|
|_InterlockedAnd16_acq|短_InterlockedAnd16_acq（短波动\*、短）|
|_InterlockedAnd16_nf|短_InterlockedAnd16_nf（短波动\*、短）|
|_InterlockedAnd16_rel|空_InterlockedAnd16_rel（短波动\*、短）|
|_InterlockedAnd64|__int64_InterlockedAnd64（_int64\_波动\*，_int64） \_|
|_InterlockedAnd64_acq|__int64_InterlockedAnd64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedAnd64_nf|__int64_InterlockedAnd64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedAnd64_rel|__int64_InterlockedAnd64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedAnd8|字符_InterlockedAnd8 （字符\*易挥发 ， 字符）|
|_InterlockedAnd8_acq|字符_InterlockedAnd8_acq （字符\*易挥发 ， 字符）|
|_InterlockedAnd8_nf|字符_InterlockedAnd8_nf （字符\*易挥发 ， 字符）|
|_InterlockedAnd8_rel|字符_InterlockedAnd8_rel （字符\*易挥发 ， 字符）|
|_InterlockedAnd_acq|长_InterlockedAnd_acq（长挥\*发性，长）|
|_InterlockedAnd_nf|长_InterlockedAnd_nf（长时间挥\*发性，长）|
|_InterlockedAnd_rel|长_InterlockedAnd_rel（长时间挥\*发性，长）|
|_InterlockedCompareExchange|长__cdecl_InterlockedCompareExchange（长挥\*发、长、长）|
|_InterlockedCompareExchange16|短_InterlockedCompareExchange16（短波动\*、短、短）|
|_InterlockedCompareExchange16_acq|短_InterlockedCompareExchange16_acq（短波动\*、短、短）|
|_InterlockedCompareExchange16_nf|短_InterlockedCompareExchange16_nf（短波动\*、短、短）|
|_InterlockedCompareExchange16_rel|短_InterlockedCompareExchange16_rel（短波动\*、短、短）|
|_InterlockedCompareExchange64|__int64_InterlockedCompareExchange64（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange64_acq|__int64_InterlockedCompareExchange64_acq（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange64_nf|__int64_InterlockedCompareExchange64_nf（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange64_rel|__int64_InterlockedCompareExchange64_rel（_int64\_波动\*、_int64、_int64） \_ \_|
|_InterlockedCompareExchange8|字符_InterlockedCompareExchange8 （字符\*易挥发， 字符， 字符）|
|_InterlockedCompareExchange8_acq|字符_InterlockedCompareExchange8_acq （字符\*易挥发， 字符， 字符）|
|_InterlockedCompareExchange8_nf|字符_InterlockedCompareExchange8_nf（字符挥\*发性，字符，字符）|
|_InterlockedCompareExchange8_rel|字符_InterlockedCompareExchange8_rel（字符挥\*发性，字符，字符）|
|_InterlockedCompareExchangePointer|空\*_InterlockedCompareExchangePointer（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchangePointer_acq|空\*_InterlockedCompareExchangePointer_acq（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchangePointer_nf|空\*_InterlockedCompareExchangePointer_nf（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchangePointer_rel|空\*_InterlockedCompareExchangePointer_rel（空\*挥\*发、\*空隙\*、空）|
|_InterlockedCompareExchange_acq|长_InterlockedCompareExchange_acq（长挥\*发、长、长）|
|_InterlockedCompareExchange_nf|长_InterlockedCompareExchange_nf（长挥\*发、长、长）|
|_InterlockedCompareExchange_rel|长_InterlockedCompareExchange_rel（长挥\*发、长、长）|
|_InterlockedDecrement|长__cdecl_InterlockedDecrement（长时间挥\*发）|
|_InterlockedDecrement16|短_InterlockedDecrement16（短挥\*发性）|
|_InterlockedDecrement16_acq|短_InterlockedDecrement16_acq（短挥\*发性）|
|_InterlockedDecrement16_nf|短_InterlockedDecrement16_nf（短波动\*）|
|_InterlockedDecrement16_rel|短_InterlockedDecrement16_rel（短挥\*发性）|
|_InterlockedDecrement64|__int64_InterlockedDecrement64（_int64\_波动\*）|
|_InterlockedDecrement64_acq|__int64_InterlockedDecrement64_acq（_int64\_波动\*）|
|_InterlockedDecrement64_nf|__int64_InterlockedDecrement64_nf（_int64\_波动\*）|
|_InterlockedDecrement64_rel|__int64_InterlockedDecrement64_rel（_int64\_波动\*）|
|_InterlockedDecrement_acq|长_InterlockedDecrement_acq（长时间挥\*发）|
|_InterlockedDecrement_nf|长_InterlockedDecrement_nf（长时间挥\*发）|
|_InterlockedDecrement_rel|长_InterlockedDecrement_rel（长时间挥\*发）|
|_InterlockedExchange|长__cdecl_InterlockedExchange（长挥\*发_Target，长）|
|_InterlockedExchange16|短_InterlockedExchange16（短波动\*_Target，短）|
|_InterlockedExchange16_acq|短_InterlockedExchange16_acq（短波动\*_Target，短）|
|_InterlockedExchange16_nf|短_InterlockedExchange16_nf（短波动\*_Target，短）|
|_InterlockedExchange64|__int64_InterlockedExchange64（_int64\_波动\*_Target，_int64） \_|
|_InterlockedExchange64_acq|__int64_InterlockedExchange64_acq（_int64\_波动\*_Target，_int64） \_|
|_InterlockedExchange64_nf|\___int64_InterlockedExchange64_nf（_int64_Target\*波动，_int64） \_|
|_InterlockedExchange8|字符_InterlockedExchange8（炭易\*挥发_Target，字符）|
|_InterlockedExchange8_acq|字符_InterlockedExchange8_acq（字符挥\*发性_Target，字符）|
|_InterlockedExchange8_nf|字符_InterlockedExchange8_nf（字符易\*失性_Target，字符）|
|_InterlockedExchangeAdd|长__cdecl_InterlockedExchangeAdd（长时间挥\*发，长）|
|_InterlockedExchangeAdd16|短_InterlockedExchangeAdd16（短波动\*、短）|
|_InterlockedExchangeAdd16_acq|短_InterlockedExchangeAdd16_acq（短波动\*、短）|
|_InterlockedExchangeAdd16_nf|短_InterlockedExchangeAdd16_nf（短波动\*、短）|
|_InterlockedExchangeAdd16_rel|短_InterlockedExchangeAdd16_rel（短波动\*、短）|
|_InterlockedExchangeAdd64|__int64_InterlockedExchangeAdd64（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd64_acq|__int64_InterlockedExchangeAdd64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd64_nf|__int64_InterlockedExchangeAdd64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd64_rel|__int64_InterlockedExchangeAdd64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedExchangeAdd8|字符_InterlockedExchangeAdd8 （字符\*易失性 ， 字符）|
|_InterlockedExchangeAdd8_acq|字符_InterlockedExchangeAdd8_acq （字符\*易挥发 ， 字符）|
|_InterlockedExchangeAdd8_nf|字符_InterlockedExchangeAdd8_nf （字符\*易挥发 ， 字符）|
|_InterlockedExchangeAdd8_rel|字符_InterlockedExchangeAdd8_rel （字符\*易挥发 ， 字符）|
|_InterlockedExchangeAdd_acq|长_InterlockedExchangeAdd_acq（长挥\*发性，长）|
|_InterlockedExchangeAdd_nf|长_InterlockedExchangeAdd_nf（长时间挥\*发性，长）|
|_InterlockedExchangeAdd_rel|长_InterlockedExchangeAdd_rel（长时间挥\*发性，长）|
|_InterlockedExchangePointer|空\*_InterlockedExchangePointer（空\*挥\*发_Target，\*空）|
|_InterlockedExchangePointer_acq|空\*_InterlockedExchangePointer_acq（空\*挥\*发_Target，\*空）|
|_InterlockedExchangePointer_nf|空\*_InterlockedExchangePointer_nf（空\*挥\*发_Target，\*空）|
|_InterlockedExchange_acq|长_InterlockedExchange_acq（长挥\*发_Target，长）|
|_InterlockedExchange_nf|长_InterlockedExchange_nf（长挥\*发_Target，长）|
|_InterlockedIncrement|长__cdecl_InterlockedIncrement（长时间挥\*发）|
|_InterlockedIncrement16|短_InterlockedIncrement16（短波动\*）|
|_InterlockedIncrement16_acq|短_InterlockedIncrement16_acq（短挥\*发性）|
|_InterlockedIncrement16_nf|短_InterlockedIncrement16_nf（短波动\*）|
|_InterlockedIncrement16_rel|短_InterlockedIncrement16_rel（短挥\*发性）|
|_InterlockedIncrement64|__int64_InterlockedIncrement64（_int64\_波动\*）|
|_InterlockedIncrement64_acq|__int64_InterlockedIncrement64_acq（_int64\_波动\*）|
|_InterlockedIncrement64_nf|__int64_InterlockedIncrement64_nf（_int64\_波动\*）|
|_InterlockedIncrement64_rel|__int64_InterlockedIncrement64_rel（_int64\_波动\*）|
|_InterlockedIncrement_acq|长_InterlockedIncrement_acq（长时间挥\*发）|
|_InterlockedIncrement_nf|长_InterlockedIncrement_nf（长时间挥\*发）|
|_InterlockedIncrement_rel|长_InterlockedIncrement_rel（长时间挥\*发）|
|_InterlockedOr|长_InterlockedOr（长时间挥\*发性，长）|
|_InterlockedOr16|短_InterlockedOr16（短波动\*、短）|
|_InterlockedOr16_acq|短_InterlockedOr16_acq（短波动\*、短）|
|_InterlockedOr16_nf|短_InterlockedOr16_nf（短波动\*、短）|
|_InterlockedOr16_rel|短_InterlockedOr16_rel（短波动\*、短）|
|_InterlockedOr64|__int64_InterlockedOr64（_int64\_波动\*，_int64） \_|
|_InterlockedOr64_acq|__int64_InterlockedOr64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedOr64_nf|__int64_InterlockedOr64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedOr64_rel|__int64_InterlockedOr64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedOr8|字符_InterlockedOr8 （字符\*易挥发 ， 字符）|
|_InterlockedOr8_acq|字符_InterlockedOr8_acq （字符\*易挥发 ， 字符）|
|_InterlockedOr8_nf|字符_InterlockedOr8_nf （字符\*易挥发 ， 字符）|
|_InterlockedOr8_rel|字符_InterlockedOr8_rel （字符\*易失性 ， 字符）|
|_InterlockedOr_acq|长_InterlockedOr_acq（长时间挥\*发性，长）|
|_InterlockedOr_nf|长_InterlockedOr_nf（长时间挥\*发性，长）|
|_InterlockedOr_rel|长_InterlockedOr_rel（长时间挥\*发性，长）|
|_InterlockedXor|长_InterlockedXor（长时间挥\*发性，长）|
|_InterlockedXor16|短_InterlockedXor16（短波动\*、短）|
|_InterlockedXor16_acq|空_InterlockedXor16_acq（短波动\*、短）|
|_InterlockedXor16_nf|短_InterlockedXor16_nf（短波动\*、短）|
|_InterlockedXor16_rel|短_InterlockedXor16_rel（短波动\*、短）|
|_InterlockedXor64|__int64_InterlockedXor64（_int64\_波动\*，_int64） \_|
|_InterlockedXor64_acq|__int64_InterlockedXor64_acq（_int64\_波动\*，_int64） \_|
|_InterlockedXor64_nf|__int64_InterlockedXor64_nf（_int64\_波动\*，_int64） \_|
|_InterlockedXor64_rel|__int64_InterlockedXor64_rel（_int64\_波动\*，_int64） \_|
|_InterlockedXor8|字符_InterlockedXor8 （字符\*易挥发 ， 字符）|
|_InterlockedXor8_acq|字符_InterlockedXor8_acq （字符\*易挥发 ， 字符）|
|_InterlockedXor8_nf|字符_InterlockedXor8_nf （字符\*易挥发 ， 字符）|
|_InterlockedXor8_rel|字符_InterlockedXor8_rel （字符\*易挥发 ， 字符）|
|_InterlockedXor_acq|长_InterlockedXor_acq（长时间挥\*发性，长）|
|_InterlockedXor_nf|长_InterlockedXor_nf（长时间挥\*发性，长）|
|_InterlockedXor_rel|长_InterlockedXor_rel（长时间挥\*发性，长）|

[[返回顶部](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest内在

纯联锁位测试内部函数是所有平台都通用的。 ARM`_acq`添加了`_rel`，`_nf`和变体，它们只是修改操作的屏障语义，如本文前面[_nf（无栅栏）后缀](#nf_suffix)中所述。

|函数名称|函数原型|
|-------------------|------------------------|
|_interlockedbittestandreset|无符号字符_interlockedbittestandreset（长时间易\*挥发，长）|
|_interlockedbittestandreset_acq|无符号字符_interlockedbittestandreset_acq（长时间易\*挥发，长）|
|_interlockedbittestandreset_nf|无符号字符_interlockedbittestandreset_nf（长时间易\*挥发，长）|
|_interlockedbittestandreset_rel|无符号字符_interlockedbittestandreset_rel（长时间易\*挥发，长）|
|_interlockedbittestandset|无符号字符_interlockedbittestandset（长时间易\*挥发，长）|
|_interlockedbittestandset_acq|无符号字符_interlockedbittestandset_acq（长时间易\*挥发，长）|
|_interlockedbittestandset_nf|无符号字符_interlockedbittestandset_nf（长时间易\*挥发，长）|
|_interlockedbittestandset_rel|无符号字符_interlockedbittestandset_rel（长时间易\*挥发，长）|

[[返回顶部](#top)]

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[ARM64 内部函数](arm64-intrinsics.md)\
[ARM 装配器参考](../assembler/arm/arm-assembler-reference.md)\
[C++语言参考](../cpp/cpp-language-reference.md)
