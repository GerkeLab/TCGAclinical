TCGA Pancancer Clinical Data
================

This repo contains the combined clinical data with follow up and outcome
data for the TCGA PanCancer Atlas in a sinlge text file and RData file.
All data in its original format can be found at
<https://gdc.cancer.gov/about-data/publications/pancanatlas>. All
original files had been previously downloaded in June of 2018.

### The PanCancer Atlas

The original
[flagship](https://www.sciencedirect.com/science/article/pii/S0092867418303027?via%3Dihub)
paper (Cell-of-Origin Patterns Dominate the Molecular Classification of
10,000 Tumors from 33 Types of Cancer by Hoadley et al) represented
efforts to provide “comprehensive integrative molecular analyses of the
complete set of tumors in TCGA”. This paper was accompanied by a paper
from [Liu et
al](https://www.cell.com/cell/pdf/S0092-8674\(18\)30229-0.pdf) (An
Integrated TCGA Pan-Cancer Clinical Data Resource to Drive High-Quality
Survival Outcome Analytics) who attempted to create a standardized
dataset for the clinical data across the PanCancer Atlas called the TCGA
Pan-Cancer Clinical Data Resource (TCGA-CDR). This was necessary as the
original TCGA project consisted of two parts 1) the pilot study which
focused on GBM, OV, and LUSC and 2) the full project which encompassed
33 cancer types. Due to the relatively short time frame of establishing
TCGA (2006-2015) clinical data is often limited and follow-up times are
short. Furthermore, the data fields available differ by cancer type as
each type had a Disease Working Group who decided what data to collect.

Thus, the PanCancer Atlas provides two data resources for clinical
annotations: `clinical_PANCAN_patient_with_followup.tsv` which is
available under Additional Resources/Supplemental Data and is not
assocaited with a specific publication and details on it’s creation are
scarce and `TCGA-CDR-SupplementalTableS1.xlsx` which is described as a
“curated resource of the clinical annotations for TCGA data and
provides recommendations for use of clinical endpoints” and comed with
the recommendation that “this file be used for clinical elements and
survival outcome data first” and is associated with the Liu et al
publication.

### Survival Data - Liu et al

Additional details on how the dataset was created can be found in the
orginial article.

“For clinical outcome endpoints, we recommend the use of **PFI** for
progression-free interval, and **OS** for overall survival. Both
endpoints are relatively accurate. Given the relatively short follow-up
time, PFI is preferred over OS. Detailed recommendations please refer to
Table 3 in the accompanying paper.”

All survival times are measured in days.

A total of 209 patients are found in `TCGA-CDR-SupplementalTableS1` but
not `clinical_PANCAN_patient_with_followup`. IDs are available below in
the missing data section.

Survival Endpoints:

  - OS - overall survival
  - DSS - disease-specific survival  
  - DFI - disease-free interval
  - PFI - progression-free
interval

<!-- For a complete description of all survival endpoint please see the the origianl data file <span style="color:purple">TCGA-CDR-SupplementalTableS1</span>.  -->

There is a strange occurence for a small subset of patients who have
secondary endpoints which occurr after their overall survival endpoint
(ie progression occurs after last followup). Patients with later DFI:
NA, TCGA-15-1444, TCGA-BR-8380, TCGA-EO-A3AY. Patients with later PFI:
NA, TCGA-UY-A9PE, TCGA-OL-A97C, TCGA-15-1444, TCGA-CW-6090,
TCGA-HW-7491, TCGA-BW-A5NP, TCGA-20-0990, TCGA-BF-A1PU, TCGA-DA-A1HW,
TCGA-BR-8380, TCGA-EO-A3AY. These numbers correspond with the data in
cBioportal, so it is not specific to this dataset. These and a handful
of other inconsistencies that have been noted are explained in further
detail in the original paper.

Supplemental Endpoints:

  - PFI.1 - progression-free interval
  - PFI.2 - progression-free interval
  - PFS - progression-free survival

Competing Risks Endpoints:

  - 0 = censored, 1 = event of interest, 2 = competing risk death
  - DSS.cr - disease-specific survival with competing risks
  - DFI.cr - disease-free interval with competing risks
  - PFI.cr - progression-free interval with competing risks
  - PFI.1.cr - progression-free interval (PFI.1) with competing risks
  - PFI.2.cr - progression-free interval (PFI.2) with competing risks

For a complete description of all survival endpoint please see the the
origianl data file `TCGA-CDR-SupplementalTableS1`.

There are now two copies of `vital_status`, `residual_tumor`, and
`margin_status`. The version from
`clinical_PANCAN_patient_with_followup` is labeled as such while the
“updated” version from `TCGA-CDR-SupplementalTableS1` (Liu et al) is
labeled as `liu_vital_status`, `liu_residual_tumor`, and
`liu_margin_status`.

## Differences within the data

There were 10956 unique patint barcodes in
`clinical_PANCAN_patient_with_followup` and 11160 unique patient
barcodes from `TCGA-CDR-SupplementalTableS1`, 10951 of which overlap,
which may account for some missingness after the two were merged, as all
patients from wither set were retained. Individual barcodes for those
missing in each dataset can be found below.

Using `vital_status` there are 7468 patients alive and 3483 who have
deceased; using `liu_vital_status` there are 7528 patients alive and
3627 deceased; using `OS` there are 7529 alive (0) and 3622 deceased
(1).

# cBioPortal

PanCancer Atlas data is also available for download at
[cBioPortal](https://www.cbioportal.org/) and
[github](https://github.com/cBioPortal/datahub/tree/master/public),
however the data has been split into individual cancer types. The
cBioPortl page points users back to the PanCancer Publications page, and
the combined PanCancer Atlas data has data available for 33 cancer types
(including LAML) and 10,953 pateints over 10,967 samples.

When using cBioPortal, to access the full PanCancer data use the
[combined
types](https://www.cbioportal.org/study/summary?id=laml_tcga_pan_can_atlas_2018%2Cacc_tcga_pan_can_atlas_2018%2Cblca_tcga_pan_can_atlas_2018%2Clgg_tcga_pan_can_atlas_2018%2Cbrca_tcga_pan_can_atlas_2018%2Ccesc_tcga_pan_can_atlas_2018%2Cchol_tcga_pan_can_atlas_2018%2Ccoadread_tcga_pan_can_atlas_2018%2Cdlbc_tcga_pan_can_atlas_2018%2Cesca_tcga_pan_can_atlas_2018%2Cgbm_tcga_pan_can_atlas_2018%2Chnsc_tcga_pan_can_atlas_2018%2Ckich_tcga_pan_can_atlas_2018%2Ckirc_tcga_pan_can_atlas_2018%2Ckirp_tcga_pan_can_atlas_2018%2Clihc_tcga_pan_can_atlas_2018%2Cluad_tcga_pan_can_atlas_2018%2Clusc_tcga_pan_can_atlas_2018%2Cmeso_tcga_pan_can_atlas_2018%2Cov_tcga_pan_can_atlas_2018%2Cpaad_tcga_pan_can_atlas_2018%2Cpcpg_tcga_pan_can_atlas_2018%2Cprad_tcga_pan_can_atlas_2018%2Csarc_tcga_pan_can_atlas_2018%2Cskcm_tcga_pan_can_atlas_2018%2Cstad_tcga_pan_can_atlas_2018%2Ctgct_tcga_pan_can_atlas_2018%2Cthym_tcga_pan_can_atlas_2018%2Cthca_tcga_pan_can_atlas_2018%2Cucs_tcga_pan_can_atlas_2018%2Cucec_tcga_pan_can_atlas_2018%2Cuvm_tcga_pan_can_atlas_2018).

When looking at cBioPortal vs PanCancer Atlas data one thing to keep in
mind is that cBioPortal reports times to events in terms of months but
doesn’t use 30.5 days in a month but instead something closer to 30.4
days in a month. Below are the overall survival time (in months) for the
full PanCancer cohort so you cna see the minor differences.

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    ##    0.00   12.46   23.34   34.03   44.85  368.92      65

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    ##    0.00   12.49   23.41   34.12   44.97  369.92      65

There are also differences in completeness of the data between the two.
For example, looking within the prostate cancer cases (PRAD) at the
variable tumor type (`Tumor Type` in cBioPortal and `tumor_type` in
PanCancer), there are 479 cases of acinar type and 15 of other type in
cBioPortal’s data but is completely missing in PanCancer.

### Missing Data

**In survival but not clinical** : TCGA-4G-AAZF, TCGA-4G-AAZG,
TCGA-4G-AAZR, TCGA-W5-AA2J, TCGA-W5-AA2K, TCGA-W5-AA2M, TCGA-W6-AA0T,
TCGA-ZH-A8Y3, TCGA-ZH-A8Y7, TCGA-AB-2802, TCGA-AB-2803, TCGA-AB-2804,
TCGA-AB-2805, TCGA-AB-2806, TCGA-AB-2807, TCGA-AB-2808, TCGA-AB-2809,
TCGA-AB-2810, TCGA-AB-2811, TCGA-AB-2812, TCGA-AB-2813, TCGA-AB-2814,
TCGA-AB-2815, TCGA-AB-2816, TCGA-AB-2817, TCGA-AB-2818, TCGA-AB-2819,
TCGA-AB-2820, TCGA-AB-2821, TCGA-AB-2822, TCGA-AB-2823, TCGA-AB-2824,
TCGA-AB-2825, TCGA-AB-2826, TCGA-AB-2827, TCGA-AB-2828, TCGA-AB-2829,
TCGA-AB-2830, TCGA-AB-2831, TCGA-AB-2832, TCGA-AB-2833, TCGA-AB-2834,
TCGA-AB-2835, TCGA-AB-2836, TCGA-AB-2837, TCGA-AB-2838, TCGA-AB-2839,
TCGA-AB-2840, TCGA-AB-2841, TCGA-AB-2842, TCGA-AB-2843, TCGA-AB-2844,
TCGA-AB-2845, TCGA-AB-2846, TCGA-AB-2847, TCGA-AB-2848, TCGA-AB-2849,
TCGA-AB-2850, TCGA-AB-2851, TCGA-AB-2853, TCGA-AB-2854, TCGA-AB-2855,
TCGA-AB-2856, TCGA-AB-2857, TCGA-AB-2858, TCGA-AB-2859, TCGA-AB-2860,
TCGA-AB-2861, TCGA-AB-2862, TCGA-AB-2863, TCGA-AB-2864, TCGA-AB-2865,
TCGA-AB-2866, TCGA-AB-2867, TCGA-AB-2868, TCGA-AB-2869, TCGA-AB-2870,
TCGA-AB-2871, TCGA-AB-2872, TCGA-AB-2873, TCGA-AB-2874, TCGA-AB-2875,
TCGA-AB-2876, TCGA-AB-2877, TCGA-AB-2878, TCGA-AB-2879, TCGA-AB-2880,
TCGA-AB-2881, TCGA-AB-2882, TCGA-AB-2883, TCGA-AB-2884, TCGA-AB-2885,
TCGA-AB-2886, TCGA-AB-2887, TCGA-AB-2888, TCGA-AB-2889, TCGA-AB-2890,
TCGA-AB-2891, TCGA-AB-2892, TCGA-AB-2893, TCGA-AB-2894, TCGA-AB-2895,
TCGA-AB-2896, TCGA-AB-2897, TCGA-AB-2898, TCGA-AB-2899, TCGA-AB-2900,
TCGA-AB-2901, TCGA-AB-2903, TCGA-AB-2904, TCGA-AB-2905, TCGA-AB-2906,
TCGA-AB-2907, TCGA-AB-2908, TCGA-AB-2909, TCGA-AB-2910, TCGA-AB-2911,
TCGA-AB-2912, TCGA-AB-2913, TCGA-AB-2914, TCGA-AB-2915, TCGA-AB-2916,
TCGA-AB-2917, TCGA-AB-2918, TCGA-AB-2919, TCGA-AB-2920, TCGA-AB-2921,
TCGA-AB-2922, TCGA-AB-2923, TCGA-AB-2924, TCGA-AB-2925, TCGA-AB-2926,
TCGA-AB-2927, TCGA-AB-2928, TCGA-AB-2929, TCGA-AB-2930, TCGA-AB-2931,
TCGA-AB-2932, TCGA-AB-2933, TCGA-AB-2934, TCGA-AB-2935, TCGA-AB-2936,
TCGA-AB-2937, TCGA-AB-2938, TCGA-AB-2939, TCGA-AB-2940, TCGA-AB-2941,
TCGA-AB-2942, TCGA-AB-2943, TCGA-AB-2944, TCGA-AB-2945, TCGA-AB-2946,
TCGA-AB-2947, TCGA-AB-2948, TCGA-AB-2949, TCGA-AB-2950, TCGA-AB-2952,
TCGA-AB-2954, TCGA-AB-2955, TCGA-AB-2956, TCGA-AB-2957, TCGA-AB-2959,
TCGA-AB-2963, TCGA-AB-2964, TCGA-AB-2965, TCGA-AB-2966, TCGA-AB-2967,
TCGA-AB-2968, TCGA-AB-2969, TCGA-AB-2970, TCGA-AB-2971, TCGA-AB-2972,
TCGA-AB-2973, TCGA-AB-2974, TCGA-AB-2975, TCGA-AB-2976, TCGA-AB-2977,
TCGA-AB-2978, TCGA-AB-2979, TCGA-AB-2980, TCGA-AB-2981, TCGA-AB-2982,
TCGA-AB-2983, TCGA-AB-2984, TCGA-AB-2985, TCGA-AB-2986, TCGA-AB-2987,
TCGA-AB-2988, TCGA-AB-2989, TCGA-AB-2990, TCGA-AB-2991, TCGA-AB-2992,
TCGA-AB-2993, TCGA-AB-2994, TCGA-AB-2995, TCGA-AB-2996, TCGA-AB-2997,
TCGA-AB-2998, TCGA-AB-2999, TCGA-AB-3000, TCGA-AB-3001, TCGA-AB-3002,
TCGA-AB-3005, TCGA-AB-3006, TCGA-AB-3007, TCGA-AB-3008, TCGA-AB-3009,
TCGA-AB-3011, TCGA-AB-3012

**In clinical but not survival** : TCGA-BH-A0B2, TCGA-E2-A1IP,
TCGA-PN-A8M9, TCGA-F5-6810, TCGA-GN-A261

### Removed variables

**All missing** : stage\_other,
history\_of\_radiation\_metastatic\_site,er\_estimated\_duration\_response,
er\_disease\_extent\_prior\_er\_treatment,er\_solid\_tumor\_response\_documented\_type,
er\_solid\_tumor\_response\_documented\_type\_other,er\_response\_type,
history\_of\_radiation\_primary\_site,history\_prior\_surgery\_type,patient\_progression\_status,
history\_prior\_surgery\_indicator,history\_prior\_surgery\_type\_other,field,
molecular\_abnormality\_results,molecular\_abnormality\_results\_other,death\_cause\_text,hbv\_test,
on\_haart\_therapy\_at\_cancer\_diagnosis,on\_haart\_therapy\_prior\_to\_cancer\_diagnosis,
hcv\_test,prior\_aids\_conditions,kshv\_hhv8\_test,days\_to\_hiv\_diagnosis,hiv\_status,
hiv\_rna\_load\_at\_diagnosis,cdc\_hiv\_risk\_group,history\_of\_other\_malignancy,history\_immunosuppresive\_dx,
nadir\_cd4\_counts,history\_relevant\_infectious\_dx\_other,history\_relevant\_infectious\_dx,
cd4\_counts\_at\_diagnosis,history\_immunological\_disease\_other,hpv\_test,
history\_immunosuppressive\_dx\_other,lost\_follow\_up,
pos\_finding\_metastatic\_breast\_carcinoma\_estrogen\_receptor\_other\_measuremenet\_scale\_text,
metastatic\_breast\_carcinoma\_pos\_finding\_progesterone\_receptor\_other\_measure\_scale\_text,
metastatic\_breast\_carcinoma\_her2\_erbb\_pos\_finding\_fluorescence\_in\_situ\_hybridization\_calculation\_method\_text,
metastatic\_breast\_carcinoma\_her2\_erbb\_method\_calculation\_method\_text,
metastatic\_breast\_carcinoma\_pos\_finding\_other\_scale\_measurement\_text

**All missing or single value** : project\_code, disease\_code,
informed\_consent\_verified,
metastatic\_breast\_carcinoma\_progesterone\_receptor\_level\_cell\_percent\_category,
metastatic\_breast\_carcinoma\_immunohistochemistry\_pr\_pos\_cell\_score,
metastatic\_breast\_carcinoma\_immunohistochemistry\_er\_pos\_cell\_score,
metastatic\_breast\_carcinoma\_her2\_erbb\_pos\_finding\_cell\_percent\_category
