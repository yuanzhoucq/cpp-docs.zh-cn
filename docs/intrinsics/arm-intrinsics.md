---
title: "ARM 内部函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, intrinsics
- intrinsics, ARM
ms.assetid: d3d7dadd-7bd5-4508-8bff-371a66913e20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c34855fa3099fa9c91badba96d39b90f4c25792b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="arm-intrinsics"></a>ARM 内部函数
Visual C++ 编译器使下面的内部函数在 ARM 架构上可用。 关于 ARM 的详细信息，请参阅[ARM 体系结构参考手册](http://go.microsoft.com/fwlink/p/?LinkId=522049)和[ARM 汇编程序工具指南](http://go.microsoft.com/fwlink/p/?LinkId=246102)ARM 信息中心网站上。  
  
##  <a name="top"></a> 霓虹灯  
 ARM 的霓虹灯矢量指令设置扩展提供了 Single Instruction Multiple Data (SIMD) 功能，这些功能类似于 x86 和 x64 架构处理器通用的 MMX 和 SSE 矢量指令中的功能。  
  
 根据头文件 `arm_neon.h`，霓虹灯内部函数受到支持。 对霓虹灯内部函数的 Visual c + + 编译器支持类似于 ARM 编译器，这记录在附录 G 中[ARM 编译器工具链、 版本 4.1 编译器参考](http://go.microsoft.com/fwlink/p/?LinkId=251083)ARM 信息中心网站上。  
  
 Visual C++ 编译器和 ARM 编译器之间的主要差别在于 Visual C++ 编译器添加了 `_ex` 的 `vldX` 变量和 `vstX` 矢量加载和存储指令。 `_ex` 变量采用附加参数，该参数指定指针参数的对齐情况但在其他方面与其非 `_ex` 对应项相同。  
  
##  <a name="A"></a> 特定于 ARM 的内部函数列表  
  
|函数名|指令|函数原型|  
|-------------------|-----------------|------------------------|  
|_arm_smlal|SMLAL|__int64 _arm_smlal(\__int64 _RdHiLo, int _Rn, int _Rm)|  
|_arm_umlal|UMLAL|无符号的 __int64 _arm_umlal (无符号\__int64 _RdHiLo，无符号的整数 _Rn，未签名的 int _Rm)|  
|_arm_clz|CLZ|unsigned int _arm_clz(unsigned int _Rm)|  
|_arm_qadd|QADD|int _arm_qadd(int _Rm, int _Rn)|  
|_arm_qdadd|QDADD|int _arm_qdadd(int _Rm, int _Rn)|  
|_arm_qdsub|QDSUB|int _arm_qdsub(int _Rm, int _Rn)|  
|_arm_qsub|QSUB|int _arm_qsub(int _Rm, int _Rn)|  
|_arm_smlabb|SMLABB|int _arm_smlabb(int _Rn, int _Rm, int _Ra)|  
|_arm_smlabt|SMLABT|int _arm_smlabt(int _Rn, int _Rm, int _Ra)|  
|_arm_smlatb|SMLATB|int _arm_smlatb(int _Rn, int _Rm, int _Ra)|  
|_arm_smlatt|SMLATT|int _arm_smlatt(int _Rn, int _Rm, int _Ra)|  
|_arm_smlalbb|SMLALBB|__int64 _arm_smlalbb(\__int64 _RdHiLo, int _Rn, int _Rm)|  
|_arm_smlalbt|SMLALBT|__int64 _arm_smlalbt(\__int64 _RdHiLo, int _Rn, int _Rm)|  
|_arm_smlaltb|SMLALTB|__int64 _arm_smlaltb(\__int64 _RdHiLo, int _Rn, int _Rm)|  
|_arm_smlaltt|SMLALTT|__int64 _arm_smlaltt(\__int64 _RdHiLo, int _Rn, int _Rm)|  
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
|_arm_smlald|SMLALD|__int64 _arm_smlald(\__int64 _RdHiLo, int _Rn, int _Rm)|  
|_arm_smlaldx|SMLALDX|__int64 _arm_smlaldx (\__int64 _RdHiLo，int _Rn int _Rm)|  
|_arm_smlsld|SMLSLD|__int64 _arm_smlsld(\__int64 _RdHiLo, int _Rn, int _Rm)|  
|_arm_smlsldx|SMLSLDX|__int64 _arm_smlsldx(\__int64 _RdHiLo, int _Rn, int _Rm)|  
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
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关的各种可以强制实施的限制的详细信息，请参阅[内存屏障限制](#BarrierRestrictions)。|  
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关的各种可以强制实施的限制的详细信息，请参阅[内存屏障限制](#BarrierRestrictions)。|  
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 将一个内存屏障操作插入指令流中。 参数 `_Type` 指定屏障强制执行的限制类型。<br /><br /> 有关的各种可以强制实施的限制的详细信息，请参阅[内存屏障限制](#BarrierRestrictions)。|  
|__emit||void __emit (无符号\__int32 操作码)<br /><br /> 将指定指令插入由编译器输出的指令流中。<br /><br /> `opcode` 的值必须是在编译时已知的常量表达式。 指令字大小为 16 位且忽略 `opcode` 最重要的 16 位。<br /><br /> 编译器在执行插入的指令前不尝试解释 `opcode` 的内容且不保证 CPU 或内存状态。<br /><br /> 编译器假定 CPU 和内存状态在执行插入的指令后保持不变。 因此，更改状态的指令会对由编译器生成的正常代码产生不利影响。<br /><br /> 出于此原因，仅使用 `emit` 插入影响编译未正常处理的 CPU 状态（如协处理器状态）的指令或执行使用 `declspec(naked)` 声明的函数。|  
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|  
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const 易失性\__int16 *)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const 易失性\__int32 *)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const 易失性\__int64 *)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const 易失性\__int8 *)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_store16||void __iso_volatile_store16(volatile \__int16 *, \__int16)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_store32||void __iso_volatile_store32(volatile \__int32 *, \__int32)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_store64||void __iso_volatile_store64(volatile \__int64 *, \__int64)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__iso_volatile_store8||void __iso_volatile_store8(volatile \__int8 *, \__int8)<br /><br /> 有关详细信息，请参阅[__iso_volatile_load/store 内部函数](#IsoVolatileLoadStore)。|  
|__ldrexd|LDREXD|__int64 \__ldrexd (const 易失性\__int64 *)|  
|__prefetch|PLD|void __cdecl \__prefetch(const void *)<br /><br /> 为系统提供一个 `PLD` 内存提示，便可很快访问指定地址处或指定地址附近的内存。 某些系统可能会选择优化此内存访问模式以提高运行时性能。 但是，从 c + + 语言的角度来看，此功能没有明显的影响，可能不执行任何操作。|  
|__rdpmccntr64||unsigned 的 __int64 \__rdpmccntr64(void)|  
|__sev|SEV|void __sev(void)|  
|__static_assert||void __static_assert(int, const char *)|  
|__swi|SVC|unsigned int __swi(unsigned int, ...)|  
|__trap|BKPT|int __trap(int, ...)|  
|__wfe|WFE|void __wfe(void)|  
|__wfi|WFI|void __wfi(void)|  
|_AddSatInt|QADD|int _AddSatInt(int, int)|  
|_CopyDoubleFromInt64||double _CopyDoubleFromInt64(\__int64)|  
|_CopyFloatFromInt32||float _CopyFloatFromInt32(\__int32)|  
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|  
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|  
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|  
|_CountLeadingOnes64||未签名的 int _CountLeadingOnes64 (无符号\__int64)|  
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|  
|_CountLeadingSigns64||无符号的整数 _CountLeadingSigns64 (\__int64)|  
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|  
|_CountLeadingZeros64||未签名的 int _CountLeadingZeros64 (无符号\__int64)|  
|_CountOneBits||unsigned int _CountOneBits(unsigned long)|  
|_CountOneBits64||未签名的 int _CountOneBits64 (无符号\__int64)|  
|_DAddSatInt|QDADD|int _DAddSatInt(int, int)|  
|_DSubSatInt|QDSUB|int _DSubSatInt(int, int)|  
|_isunordered||int _isunordered(double, double)|  
|_isunorderedf||int _isunorderedf(float, float)|  
|_MoveFromCoprocessor|MRC|unsigned int _MoveFromCoprocessor(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息请参阅[_MoveFromCoprocessor，_MoveFromCoprocessor2](#MoveFromCo)。|  
|_MoveFromCoprocessor2|MRC2|unsigned int _MoveFromCoprocessor2(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息请参阅[_MoveFromCoprocessor，_MoveFromCoprocessor2](#MoveFromCo)。|  
|_MoveFromCoprocessor64|MRRC|unsigned __int64 _MoveFromCoprocessor64(unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息请参阅[_MoveFromCoprocessor64](#MoveFromCo64)。|  
|_MoveToCoprocessor|MCR|void _MoveToCoprocessor(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息请参阅[_MoveToCoprocessor，_MoveToCoprocessor2](#MoveToCo)。|  
|_MoveToCoprocessor2|MCR2|void _MoveToCoprocessor2(unsigned int, unsigned int, unsigned int, unsigned int, unsigned int, unsigned int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息请参阅[_MoveToCoprocessor，_MoveToCoprocessor2](#MoveToCo)。|  
|_MoveToCoprocessor64|MCRR|void _MoveToCoprocessor64 (无符号\__int64，无符号 int、 unsigned int、 未签名的 int)<br /><br /> 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。 有关详细信息请参阅[_MoveToCoprocessor64](#MoveToCo64)。|  
|_MulHigh||long _MulHigh(long, long)|  
|_MulUnsignedHigh||unsigned long _MulUnsignedHigh(unsigned long, unsigned long)|  
|_ReadBankedReg|MRS|int _ReadBankedReg(int _Reg)|  
|_ReadStatusReg|MRS|int _ReadStatusReg(int)|  
|_SubSatInt|QSUB|int _SubSatInt(int, int)|  
|_WriteBankedReg|MSR|void _WriteBankedReg(int _Value, int _Reg)|  
|_WriteStatusReg|MSR|void _WriteStatusReg(int, int, int)|  
  
 [[NEON](#top)]  
  
###  <a name="BarrierRestrictions"></a> 内存屏障限制  
 内部函数 `__dmb`（数据内存屏障）、`__dsb`（数据同步屏障）和 `__isb`（指令同步屏障）使用以下预定义值以根据共享域和受操作影响的访问类型对内存屏障限制进行指定。  
  
|限制值|描述|  
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
  
###  <a name="IsoVolatileLoadStore"></a> __iso_volatile_load/store 内部函数  
 这些内部函数显式执行不进行编译器优化的加载和存储。  
  
```  
__int16 __iso_volatile_load16(const volatile __int16 * Location)  
__int32 __iso_volatile_load32(const volatile __int32 * Location)  
__int64 __iso_volatile_load64(const volatile __int64 * Location)  
__int8 __iso_volatile_load8(const volatile __int8 * Location)  
  
void __iso_volatile_store16(volatile __int16 * Location, __int16 Value)  
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value)  
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value)  
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value)  
  
```  
  
 **参数**  
  
 `Location`  
 要从中读取或为其写入的内存位置的地址。  
  
 `Value`（仅存储内部函数）  
 要写入到指定内存位置的值。  
  
 **返回值 （仅加载内部函数）**  
  
 由 `Location` 指定的内存位置的值。  
  
 **备注**  
  
 你可以使用 `__iso_volatile_load8/16/32/64` 和 `__iso_volatile_store8/16/32/64` 内存函数显式执行不进行编译器优化的内存访问。 编译器不能删除、同步或更改这些操作的相对顺序，但不会生成隐式硬件内存屏障。 因此，硬件仍可能对跨多个线程的可观察内存访问进行重新排序。 更确切地说，这些内部函数是等效于以下表达式下编译**/volatile:iso**。  
  
```  
  
      int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;   
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;  
```  
  
 请注意内部函数采用易失性指针来适应易失性变量。 但是，不要求或不建议将易失性指针用作自变量；如果使用常规、非易失性类型，则这些操作的语义完全相同。  
  
 有关详细信息**/volatile:iso**命令行参数，请参阅[/volatile （volatile 关键字解释）](../build/reference/volatile-volatile-keyword-interpretation.md)。  
  
###  <a name="MoveFromCo"></a> _MoveFromCoprocessor _MoveFromCoprocessor2  
 这些内部函数通过使用协处理器数据传输指令从 ARM 协处理器读取数据。  
  
```  
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
  
 **参数**  
  
 `coproc`  
 0 到 15 之间的协处理器编号。  
  
 `opcode1`  
 0 到 7 之间特定于协处理器的操作码  
  
 `crn`  
 协处理器寄存器编号，在 0 到 15 之间，用于向指令指定第一个操作数。  
  
 `crm`  
 协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。  
  
 `opcode2`  
 0 到 7 之间特定于附加协处理器的操作码。  
  
 **返回值**  
  
 从协处理器中读取的值。  
  
 **备注**  
  
 此内部函数的所有五个参数的值必须是在编译时已知的常量表达式。  
  
 `_MoveFromCoprocessor` 使用 MRC 指令；`_MoveFromCoprocessor2` 使用 MRC2。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。  
  
###  <a name="MoveFromCo64"></a> _MoveFromCoprocessor64  
 使用协处理器数据传输指令，读取 ARM 协处理器中的数据。  
  
```  
unsigned __int64 _MoveFromCoprocessor64(  
      unsigned int coproc,  
      unsigned int opcode1,  
      unsigned int crm,  
);  
  
```  
  
 **参数**  
  
 `coproc`  
 0 到 15 之间的协处理器编号。  
  
 `opcode1`  
 0 到 15 之间特定于协处理器的操作码。  
  
 `crm`  
 协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。  
  
 **返回值**  
  
 从协处理器中读取的值。  
  
 **备注**  
  
 此内部函数的所有三个参数的值必须是在编译时已知的常量表达式。  
  
 `_MoveFromCoprocessor64` 使用 MRRC 指令。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。  
  
###  <a name="MoveToCo"></a> _MoveToCoprocessor _MoveToCoprocessor2  
 这些内部函数通过使用协处理器数据传输指令将数据写入到 ARM 协处理器。  
  
```  
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
  
 **参数**  
  
 `value`  
 要写入到协处理器的值。  
  
 `coproc`  
 0 到 15 之间的协处理器编号。  
  
 `opcode1`  
 0 到 7 之间特定于协处理器的操作码。  
  
 `crn`  
 协处理器寄存器编号，在 0 到 15 之间，用于向指令指定第一个操作数。  
  
 `crm`  
 协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。  
  
 `opcode2`  
 0 到 7 之间特定于附加协处理器的操作码。  
  
 **返回值**  
  
 无。  
  
 **备注**  
  
 此内部函数的 `coproc`、`opcode1`、`crn`、`crm` 和 `opcode2` 参数的值必须是在编译时已知的常量表达式。  
  
 `_MoveToCoprocessor` 使用 MCR 指令；`_MoveToCoprocessor2` 使用 MCR2。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。  
  
###  <a name="MoveToCo64"></a> _MoveToCoprocessor64  
 这些内部函数通过使用协处理器数据传输指令将数据写入到 ARM 协处理器。  
  
```  
void _MoveFromCoprocessor64(  
      unsigned __int64 value,  
      unsigned int coproc,  
      unsigned int opcode1,  
      unsigned int crm,  
);  
  
```  
  
 **参数**  
  
 `coproc`  
 0 到 15 之间的协处理器编号。  
  
 `opcode1`  
 0 到 15 之间特定于协处理器的操作码。  
  
 `crm`  
 协处理器寄存器编号，在 0 到 15 之间，用于指定附加的源或目标操作数。  
  
 **返回值**  
  
 无。  
  
 **备注**  
  
 此内部函数的 `coproc`、`opcode1` 和 `crm` 参数的值必须是编译时已知的常量表达式。  
  
 `_MoveFromCoprocessor64` 使用 MCRR 指令。 此参数对应于直接编码到指令字中的位字段。 参数的解释与协处理器相关。 有关详细信息，请参见有问题的协处理器的手册。  
  
##  <a name="I"></a> ARM 支持来自其他体系结构的内部函数  
 下表列出了来自在 ARM 平台上受支持的其他体系结构的内部函数。 如果 ARM 上的内部函数行为不同于它在其他硬件体系结构上的行为，则记录其他详细信息。  
  
|函数名|函数原型|  
|-------------------|------------------------|  
|__assume|void __assume(int)|  
|__code_seg|void __code_seg(const char *)|  
|__debugbreak|void __cdecl \__debugbreak(void)|  
|__fastfail|__declspec （noreturn) void \__fastfail （无符号整数）|  
|__nop|void __nop(void)**注意：**在 ARM 平台上，如果在目标体系结构中实现了一个，此函数将生成一个 NOP 指令; 否则，一个替代指令，不会更改项目或 CPU 的状态为生成 — 例如， `MOV r8, r8`。 这在功能上等效于\__nop 其他硬件体系结构内部函数。 因为对项目或 CPU 的状态无影响的指令可能会因优化而被目标体系结构忽略，所以指令不一定消耗 CPU 周期。 因此，不要使用\__nop 内部函数来操作代码序列的执行时间，除非确信 CPU 的工作方式。 相反，你可以使用\__nop 内部对齐到特定的 32 位边界地址的下一个指令。|  
|__yield|void __yield(void)**注意：**在 ARM 平台上，此函数生成 YIELD 指令，这表示线程正在执行从执行的任务可以暂时挂起 — 例如，旋转锁 — 而无需对项目产生负面影响。 这使 CPU 可在执行周期过程中执行其他任务，这些任务如果不执行则会被浪费掉。|  
|_AddressOfReturnAddress|void * _AddressOfReturnAddress(void)|  
|_BitScanForward|unsigned char _BitScanForward(unsigned long * _Index, unsigned long _Mask)|  
|_BitScanReverse|unsigned char _BitScanReverse(unsigned long * _Index, unsigned long _Mask)|  
|_bittest|unsigned char _bittest(long const *, long)|  
|_bittestandcomplement|unsigned char _bittestandcomplement(long *, long)|  
|_bittestandreset|unsigned char _bittestandreset(long *, long)|  
|_bittestandset|unsigned char _bittestandset(long *, long)|  
|_byteswap_uint64|unsigned 的 __int64 \__cdecl _byteswap_uint64 (无符号\__int64)|  
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|  
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|  
|_disable|void __cdecl _disable(void)**注意：**在 ARM 平台上，此函数生成 CPSID 指令; 仅可用作内部函数。|  
|_enable|void __cdecl _enable(void)**注意：**在 ARM 平台上，此函数生成 CPSIE 指令; 仅可用作内部函数。|  
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|  
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|  
|_ReadBarrier|void _ReadBarrier(void)|  
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|  
|_ReturnAddress|void * _ReturnAddress(void)|  
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|  
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|  
|_rotl64|unsigned 的 __int64 \__cdecl _rotl64 (无符号\__int64 _Value，int _Shift)|  
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|  
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|  
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|  
|_rotr64|unsigned 的 __int64 \__cdecl _rotr64 (无符号\__int64 _Value，int _Shift)|  
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|  
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|  
|_WriteBarrier|void _WriteBarrier(void)|  
  
 [[NEON](#top)]  
  
## <a name="interlocked-intrinsics"></a>互锁内部函数  
 互锁内部函数是用于执行原子读取-修改-写入操作的一组内部函数。 其中一些互锁内部函数通用于所有平台。 此处单独将其列出不是因为它们数量庞大，而是因为它们的定义通常是多余的，一般情况下较容易就想到它们。 它们的名称可用于派生确切行为。  
  
 下表总结了非 bittest 互锁内部函数的 ARM 支持。 表中的每个单元格都对应一个名称，这些名称的派生方式是将该行的最左侧单元格中的操作名和该列的最上面单元格中的类型名附加到 `_Interlocked`。 例如的交叉点处的单元格`Xor`行和**8**列都对应于`_InterlockedXor8`和完全支持。 大部分受支持的函数提供以下可选后缀：`_acq`、`_rel` 和 `_nf`。 `_acq` 后缀表示“获取”语义，而 `_rel` 后缀表示“发布”语义。 `_nf` 或“no fence”后缀对于 ARM 来说是唯一的，我们将在下一节进行讨论。  
  
||8|16|32|64|P|  
|-|-------|--------|--------|--------|-------|  
|添加|无|无|完全|完全|无|  
|And|完全|完全|完全|完全|无|  
|CompareExchange|完全|完全|完全|完全|完全|  
|递减|无|完全|完全|完全|无|  
|交换|部分|部分|部分|部分|部分|  
|ExchangeAdd|完全|完全|完全|完全|无|  
|递增|无|完全|完全|完全|无|  
|Or|完全|完全|完全|完全|无|  
|Xor|完全|完全|完全|完全|无|  
  
 密钥：  
  
-   **完整**： 支持无格式、 `_acq`， `_rel`，和`_nf`窗体。  
  
-   **部分**： 支持无格式、 `_acq`，和`_nf`窗体。  
  
-   **无**： 不支持  
  
###  <a name="nf_suffix"></a> _nf （无围墙） 后缀  
 `_nf` 或“no fence”后缀表示此操作未表现为任何类型的内存屏障。 这与表现为某种屏障的其他三种窗体（无格式、`_acq` 和 `_rel`）相反。 `_nf` 窗体可用于保持统计信息计数器，该计数器由多个线程同时更新但在执行多个线程时不使用该计数器的值。  
  
### <a name="list-of-interlocked-intrinsics"></a>互锁内部函数列表  
  
|函数名|函数原型|  
|-------------------|------------------------|  
|_InterlockedAdd|long _InterlockedAdd(long _volatile *, long)|  
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\__int64 volatile *， \__int64)|  
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq(\__int64 volatile *, \__int64)|  
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\__int64 volatile *， \__int64)|  
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\__int64 volatile *， \__int64)|  
|_InterlockedAdd_acq|long _InterlockedAdd_acq(long volatile *, long)|  
|_InterlockedAdd_nf|long _InterlockedAdd_nf(long volatile *, long)|  
|_InterlockedAdd_rel|long _InterlockedAdd_rel(long volatile *, long)|  
|_InterlockedAnd|long _InterlockedAnd(long volatile *, long)|  
|_InterlockedAnd16|short _InterlockedAnd16(short volatile *, short)|  
|_InterlockedAnd16_acq|short _InterlockedAnd16_acq(short volatile *, short)|  
|_InterlockedAnd16_nf|short _InterlockedAnd16_nf(short volatile *, short)|  
|_InterlockedAnd16_rel|short _InterlockedAnd16_rel(short volatile *, short)|  
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\__int64 volatile *， \__int64)|  
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq(\__int64 volatile *, \__int64)|  
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\__int64 volatile *， \__int64)|  
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\__int64 volatile *， \__int64)|  
|_InterlockedAnd8|char _InterlockedAnd8(char volatile *, char)|  
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq(char volatile *, char)|  
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf(char volatile *, char)|  
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel(char volatile *, char)|  
|_InterlockedAnd_acq|long _InterlockedAnd_acq(long volatile *, long)|  
|_InterlockedAnd_nf|long _InterlockedAnd_nf(long volatile *, long)|  
|_InterlockedAnd_rel|long _InterlockedAnd_rel(long volatile *, long)|  
|_InterlockedCompareExchange|long __cdecl _InterlockedCompareExchange(long volatile *, long, long)|  
|_InterlockedCompareExchange16|short _InterlockedCompareExchange16(short volatile *, short, short)|  
|_InterlockedCompareExchange16_acq|short _InterlockedCompareExchange16_acq(short volatile *, short, short)|  
|_InterlockedCompareExchange16_nf|short _InterlockedCompareExchange16_nf(short volatile *, short, short)|  
|_InterlockedCompareExchange16_rel|short _InterlockedCompareExchange16_rel(short volatile *, short, short)|  
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\__int64 volatile *， \__int64， \__int64)|  
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\__int64 volatile *， \__int64， \__int64)|  
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\__int64 volatile *， \__int64， \__int64)|  
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\__int64 volatile *， \__int64， \__int64)|  
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8(char volatile *, char, char)|  
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq(char volatile *, char, char)|  
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf(char volatile *, char, char)|  
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel(char volatile *, char, char)|  
|_InterlockedCompareExchangePointer|void * _InterlockedCompareExchangePointer (void\*易失性\*，void \*，void \*)|  
|_InterlockedCompareExchangePointer_acq|void * _InterlockedCompareExchangePointer_acq(void \* volatile \*, void \*, void \*)|  
|_InterlockedCompareExchangePointer_nf|void * _InterlockedCompareExchangePointer_nf (void\*易失性\*，void \*，void \*)|  
|_InterlockedCompareExchangePointer_rel|void * _InterlockedCompareExchangePointer_rel (void\*易失性\*，void \*，void \*)|  
|_InterlockedCompareExchange_acq|long _InterlockedCompareExchange_acq(long volatile *, long, long)|  
|_InterlockedCompareExchange_nf|long _InterlockedCompareExchange_nf(long volatile *, long, long)|  
|_InterlockedCompareExchange_rel|long _InterlockedCompareExchange_rel(long volatile *, long, long)|  
|_InterlockedDecrement|long __cdecl _InterlockedDecrement(long volatile *)|  
|_InterlockedDecrement16|short _InterlockedDecrement16(short volatile *)|  
|_InterlockedDecrement16_acq|short _InterlockedDecrement16_acq(short volatile *)|  
|_InterlockedDecrement16_nf|short _InterlockedDecrement16_nf(short volatile *)|  
|_InterlockedDecrement16_rel|short _InterlockedDecrement16_rel(short volatile *)|  
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 易失性 *)|  
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq(\__int64 volatile *)|  
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf(\__int64 volatile *)|  
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 易失性 *)|  
|_InterlockedDecrement_acq|long _InterlockedDecrement_acq(long volatile *)|  
|_InterlockedDecrement_nf|long _InterlockedDecrement_nf(long volatile *)|  
|_InterlockedDecrement_rel|long _InterlockedDecrement_rel(long volatile *)|  
|_InterlockedExchange|long __cdecl _InterlockedExchange(long volatile * _Target, long)|  
|_InterlockedExchange16|short _InterlockedExchange16(short volatile * _Target, short)|  
|_InterlockedExchange16_acq|short _InterlockedExchange16_acq(short volatile * _Target, short)|  
|_InterlockedExchange16_nf|short _InterlockedExchange16_nf(short volatile * _Target, short)|  
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\__int64 易失性 * _Target， \__int64)|  
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\__int64 易失性 * _Target， \__int64)|  
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\__int64 易失性 * _Target， \__int64)|  
|_InterlockedExchange8|char _InterlockedExchange8(char volatile * _Target, char)|  
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq(char volatile * _Target, char)|  
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf(char volatile * _Target, char)|  
|_InterlockedExchangeAdd|long __cdecl _InterlockedExchangeAdd(long volatile *, long)|  
|_InterlockedExchangeAdd16|short _InterlockedExchangeAdd16(short volatile *, short)|  
|_InterlockedExchangeAdd16_acq|short _InterlockedExchangeAdd16_acq(short volatile *, short)|  
|_InterlockedExchangeAdd16_nf|short _InterlockedExchangeAdd16_nf(short volatile *, short)|  
|_InterlockedExchangeAdd16_rel|short _InterlockedExchangeAdd16_rel(short volatile *, short)|  
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (\__int64 volatile *， \__int64)|  
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq(\__int64 volatile *, \__int64)|  
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf(\__int64 volatile *, \__int64)|  
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel(\__int64 volatile *, \__int64)|  
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8(char volatile *, char)|  
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq(char volatile *, char)|  
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf(char volatile *, char)|  
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel(char volatile *, char)|  
|_InterlockedExchangeAdd_acq|long _InterlockedExchangeAdd_acq(long volatile *, long)|  
|_InterlockedExchangeAdd_nf|long _InterlockedExchangeAdd_nf(long volatile *, long)|  
|_InterlockedExchangeAdd_rel|long _InterlockedExchangeAdd_rel(long volatile *, long)|  
|_InterlockedExchangePointer|void * _InterlockedExchangePointer (void\*易失性\*_Target，void \*)|  
|_InterlockedExchangePointer_acq|void * _InterlockedExchangePointer_acq (void\*易失性\*_Target，void \*)|  
|_InterlockedExchangePointer_nf|void * _InterlockedExchangePointer_nf (void\*易失性\*_Target，void \*)|  
|_InterlockedExchange_acq|long _InterlockedExchange_acq(long volatile * _Target, long)|  
|_InterlockedExchange_nf|long _InterlockedExchange_nf(long volatile * _Target, long)|  
|_InterlockedIncrement|long __cdecl _InterlockedIncrement(long volatile *)|  
|_InterlockedIncrement16|short _InterlockedIncrement16(short volatile *)|  
|_InterlockedIncrement16_acq|short _InterlockedIncrement16_acq(short volatile *)|  
|_InterlockedIncrement16_nf|short _InterlockedIncrement16_nf(short volatile *)|  
|_InterlockedIncrement16_rel|short _InterlockedIncrement16_rel(short volatile *)|  
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\__int64 易失性 *)|  
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq(\__int64 volatile *)|  
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf(\__int64 volatile *)|  
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\__int64 易失性 *)|  
|_InterlockedIncrement_acq|long _InterlockedIncrement_acq(long volatile *)|  
|_InterlockedIncrement_nf|long _InterlockedIncrement_nf(long volatile *)|  
|_InterlockedIncrement_rel|long _InterlockedIncrement_rel(long volatile *)|  
|_InterlockedOr|long _InterlockedOr(long volatile *, long)|  
|_InterlockedOr16|short _InterlockedOr16(short volatile *, short)|  
|_InterlockedOr16_acq|short _InterlockedOr16_acq(short volatile *, short)|  
|_InterlockedOr16_nf|short _InterlockedOr16_nf(short volatile *, short)|  
|_InterlockedOr16_rel|short _InterlockedOr16_rel(short volatile *, short)|  
|_InterlockedOr64|__int64 _InterlockedOr64 (\__int64 volatile *， \__int64)|  
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq(\__int64 volatile *, \__int64)|  
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf(\__int64 volatile *, \__int64)|  
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\__int64 volatile *， \__int64)|  
|_InterlockedOr8|char _InterlockedOr8(char volatile *, char)|  
|_InterlockedOr8_acq|char _InterlockedOr8_acq(char volatile *, char)|  
|_InterlockedOr8_nf|char _InterlockedOr8_nf(char volatile *, char)|  
|_InterlockedOr8_rel|char _InterlockedOr8_rel(char volatile *, char)|  
|_InterlockedOr_acq|long _InterlockedOr_acq(long volatile *, long)|  
|_InterlockedOr_nf|long _InterlockedOr_nf(long volatile *, long)|  
|_InterlockedOr_rel|long _InterlockedOr_rel(long volatile *, long)|  
|_InterlockedXor|long _InterlockedXor(long volatile *, long)|  
|_InterlockedXor16|short _InterlockedXor16(short volatile *, short)|  
|_InterlockedXor16_acq|short _InterlockedXor16_acq(short volatile *, short)|  
|_InterlockedXor16_nf|short _InterlockedXor16_nf(short volatile *, short)|  
|_InterlockedXor16_rel|short _InterlockedXor16_rel(short volatile *, short)|  
|_InterlockedXor64|__int64 _InterlockedXor64 (\__int64 volatile *， \__int64)|  
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (\__int64 volatile *， \__int64)|  
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\__int64 volatile *， \__int64)|  
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\__int64 volatile *， \__int64)|  
|_InterlockedXor8|char _InterlockedXor8(char volatile *, char)|  
|_InterlockedXor8_acq|char _InterlockedXor8_acq(char volatile *, char)|  
|_InterlockedXor8_nf|char _InterlockedXor8_nf(char volatile *, char)|  
|_InterlockedXor8_rel|char _InterlockedXor8_rel(char volatile *, char)|  
|_InterlockedXor_acq|long _InterlockedXor_acq(long volatile *, long)|  
|_InterlockedXor_nf|long _InterlockedXor_nf(long volatile *, long)|  
|_InterlockedXor_rel|long _InterlockedXor_rel(long volatile *, long)|  
  
 [[NEON](#top)]  
  
### <a name="interlockedbittest-intrinsics"></a>_interlockedbittest 内部函数  
 纯互锁的 bittest 内部函数通用于所有平台。 ARM 添加`_acq`， `_rel`，和`_nf`中所述，只需修改操作的屏障语义的变体[_nf （无围墙） 后缀](#nf_suffix)本文前面。  
  
|函数名|函数原型|  
|-------------------|------------------------|  
|_interlockedbittestandreset|unsigned char _interlockedbittestandreset(long volatile *, long)|  
|_interlockedbittestandreset_acq|unsigned char _interlockedbittestandreset_acq(long volatile *, long)|  
|_interlockedbittestandreset_nf|unsigned char _interlockedbittestandreset_nf(long volatile *, long)|  
|_interlockedbittestandreset_rel|unsigned char _interlockedbittestandreset_rel(long volatile *, long)|  
|_interlockedbittestandset|unsigned char _interlockedbittestandset(long volatile *, long)|  
|_interlockedbittestandset_acq|unsigned char _interlockedbittestandset_acq(long volatile *, long)|  
|_interlockedbittestandset_nf|unsigned char _interlockedbittestandset_nf(long volatile *, long)|  
|_interlockedbittestandset_rel|unsigned char _interlockedbittestandset_rel(long volatile *, long)|  
  
 [[NEON](#top)]  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [ARM 汇编程序参考](../assembler/arm/arm-assembler-reference.md)   
 [C++ 语言参考](../cpp/cpp-language-reference.md)