# Example SLURM log file
The following is an example slurm log file for a suceessful run of cleansumstats

```
Starting job 13695822 on c2-1 at Mon Feb 28 09:36:22 CET 2022

35
COGENT_COG_2017
/cluster/projects/p697/projects/SUMSTATv2_RAW/COGENT_COG_2017/COGENT_COG_2017.cleansumstats_meta /cluster/projects/p697/projects/SUMSTATv2_RAW/COGENT_COG_2017_noCHARGE/COGENT_COG_2017_noCHARGE.cleansumstats_meta /cluster/projects/p697/projects/SUMSTATv2_RAW/COGENT_COG_2017_noTOP/COGENT_COG_2017_noTOP.cleansumstats_meta
COGENT_COG_2017
mkdir: cannot create directory ‘/cluster/projects/p697/users/michaejt/SUMSTATv2_dev/cleansumstats/COGENT_COG_2017’: File exists
mkdir: cannot create directory ‘/tsd/p697/home/p697-michaejt/p697code/scratch/COGENT_COG_2017’: File exists
-------------------------------------------------------------------------------
There are messages associated with the following module(s):
-------------------------------------------------------------------------------

singularity/3.7.1:
   This is a custom module. You can use "module spider <software>" to search
   for more recent Easybuild modules (those listed under
   /cluster/software/MODULEFILES/easybuild/all). If no recent Easybuild
   module is available, you can request it to be installed:
   https://nettskjema.no/a/usit-sw-request#/page/1

-------------------------------------------------------------------------------

N E X T F L O W  ~  version 21.12.1-edge
Launching `/cleansumstats/main.nf` [sick_gates] - revision: ef09f3f0cb
----------------------------------------------------
                                        ,--./,-.
                                        `._,._,'
 cleansumstats v1.3.0
----------------------------------------------------

Run Name          : sick_gates
Input             : /cleansumstats/input/COGENT_COG_2017.cleansumstats_meta
Max Resources     : 400 GB memory, 60 cpus, 4h time per job
Output dir        : /cleansumstats/outdir
Launch dir        : /cleansumstats/tmp/fake-home
Working dir       : /cleansumstats/work
Script dir        : /cleansumstats
User              : p697-michaejt
Config Profile    : standard
----------------------------------------------------
Reading metadata files
Postprocess metadata
Successfully read/validated metadata file '/cleansumstats/input/COGENT_COG_2017.cleansumstats_meta'
All metadata files read
Validating pipeline parameters
All pipeline parameters validated
[-        ] process > calculate_checksum_on_metaf... -
[-        ] process > calculate_checksum_on_sumst... -
[-        ] process > make_metafile_unix_friendly    -
[-        ] process > check_sumstat_format           -
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -

[-        ] process > calculate_checksum_on_metaf... -
[-        ] process > calculate_checksum_on_sumst... -
[-        ] process > make_metafile_unix_friendly    -
[-        ] process > check_sumstat_format           -
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (4)
[5c/ad391a] process > calculate_checksum_on_metaf... [  0%] 0 of 1
[71/c1ce86] process > calculate_checksum_on_sumst... [  0%] 0 of 1
[62/52480d] process > make_metafile_unix_friendly... [  0%] 0 of 1
[ef/29262c] process > check_sumstat_format (1)       [  0%] 0 of 1
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (4)
[5c/ad391a] process > calculate_checksum_on_metaf... [  0%] 0 of 1
[71/c1ce86] process > calculate_checksum_on_sumst... [  0%] 0 of 1
[62/52480d] process > make_metafile_unix_friendly... [  0%] 0 of 1
[ef/29262c] process > check_sumstat_format (1)       [  0%] 0 of 1
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (4)
[5c/ad391a] process > calculate_checksum_on_metaf... [  0%] 0 of 1
[71/c1ce86] process > calculate_checksum_on_sumst... [  0%] 0 of 1
[62/52480d] process > make_metafile_unix_friendly... [  0%] 0 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [  0%] 0 of 1
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (4)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [  0%] 0 of 1
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [  0%] 0 of 1
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (4)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [  0%] 0 of 1
[-        ] process > add_sorted_rowindex_to_sumstat -
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (5)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:prepare_dbsnp_... -
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:is_chrpos_diff... -
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[-        ] process > update_stats:numeric_filter... -
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (8)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:remove_duplica... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:reformat_chrom... -
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (12)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [  0%] 0 of 1
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [  0%] 0 of 2
[-        ] process > map_to_dbsnp:detect_genome_... -
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (16)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[b1/c52759] process > map_to_dbsnp:detect_genome_... [  0%] 0 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (16)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[b1/c52759] process > map_to_dbsnp:detect_genome_... [  0%] 0 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (16)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[80/2e1e02] process > map_to_dbsnp:detect_genome_... [ 25%] 1 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (16)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[0d/3c4f06] process > map_to_dbsnp:detect_genome_... [ 50%] 2 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (16)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[b1/c52759] process > map_to_dbsnp:detect_genome_... [ 75%] 3 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [  0%] 0 of 1
[-        ] process > update_stats:convert_neglogP   -
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (17)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[b1/c52759] process > map_to_dbsnp:detect_genome_... [ 75%] 3 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [  0%] 0 of 1
[-        ] process > update_stats:force_eaf         -
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (18)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[b1/c52759] process > map_to_dbsnp:detect_genome_... [ 75%] 3 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [  0%] 0 of 1
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (18)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[b1/c52759] process > map_to_dbsnp:detect_genome_... [ 75%] 3 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (18)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[82/4112f8] process > map_to_dbsnp:detect_genome_... [100%] 4 of 4
[-        ] process > map_to_dbsnp:decide_genome_... -
[-        ] process > map_to_dbsnp:build_warning     -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (21)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[82/4112f8] process > map_to_dbsnp:detect_genome_... [100%] 4 of 4
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [  0%] 0 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:maplift_dbsnp_... -
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (22)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[82/4112f8] process > map_to_dbsnp:detect_genome_... [100%] 4 of 4
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (22)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[e0/891e60] process > map_to_dbsnp:reformat_chrom... [ 50%] 1 of 2
[82/4112f8] process > map_to_dbsnp:detect_genome_... [100%] 4 of 4
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (22)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[82/4112f8] process > map_to_dbsnp:detect_genome_... [100%] 4 of 4
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (26)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[5d/22ec77] process > map_to_dbsnp:detect_genome_... [ 50%] 4 of 8
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (26)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[32/0d2d13] process > map_to_dbsnp:detect_genome_... [ 62%] 5 of 8
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (26)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[5d/22ec77] process > map_to_dbsnp:detect_genome_... [ 75%] 6 of 8
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (26)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[4c/612dbf] process > map_to_dbsnp:detect_genome_... [ 87%] 7 of 8
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [100%] 1 of 1
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (26)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[ed/cd1754] process > map_to_dbsnp:decide_genome_... [ 50%] 1 of 2
[ee/dd360c] process > map_to_dbsnp:build_warning (1) [100%] 1 of 1
[f0/60056a] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (29)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [ 50%] 1 of 2
[6b/f47a10] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (30)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [ 50%] 1 of 2
[-        ] process > map_to_dbsnp:select_chrpos_... -
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (31)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (31)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:rm_dup_chrpos_... -
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (32)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:reformat_sumstat  -
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (33)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (33)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [  0%] 0 of 1
[-        ] process > map_to_dbsnp:split_multiall... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (34)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [  0%] 0 of 1
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (34)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [  0%] 0 of 1
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (35)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [  0%] 0 of 1
[-        ] process > allele_correction:allele_co... -
[-        ] process > allele_correction:rm_dup_ch... -
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[-        ] process > organize_output:collect_rmd... -
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (37)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [  0%] 0 of 1
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[-        ] process > update_stats:prep_af_stats     -
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [  0%] 0 of 1
[-        ] process > organize_output:desc_rmd_li... -
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (39)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [  0%] 0 of 1
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [  0%] 0 of 1
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (39)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [  0%] 0 of 1
[-        ] process > update_stats:add_af_stats      -
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (40)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [  0%] 0 of 1
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (40)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[-        ] process > update_stats:infer_stats       -
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (42)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [  0%] 0 of 2
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (42)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[53/baf432] process > update_stats:infer_stats (1)   [ 50%] 1 of 2
[-        ] process > update_stats:merge_inferred... -
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (43)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [  0%] 0 of 1
[-        ] process > update_stats:select_stats_f... -
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (44)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [  0%] 0 of 1
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (44)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[-        ] process > organize_output:final_assembly -
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (45)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [  0%] 0 of 1
[-        ] process > organize_output:prep_GRCh37... -
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[-        ] process > organize_output:collect_and... -
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (47)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [  0%] 0 of 1
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[a4/a5410a] process > organize_output:collect_and... [  0%] 0 of 1
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (47)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [  0%] 0 of 1
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[-        ] process > organize_output:gzip_outfiles  -
[-        ] process > organize_output:calculate_c... -
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (48)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [  0%] 0 of 1
[-        ] process > organize_output:calculate_c... -
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (48)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [  0%] 0 of 1
[-        ] process > organize_output:calculate_c... -
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[-        ] process > organize_output:prepare_cle... -
[-        ] process > organize_output:add_raw_to_... -
[-        ] process > organize_output:add_details... -
[-        ] process > organize_output:add_cleaned... -

executor >  local (51)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [100%] 1 of 1 ✔
[59/7f44c9] process > organize_output:calculate_c... [  0%] 0 of 1
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[-        ] process > organize_output:prepare_cle... -
[ab/1e5f7d] process > organize_output:add_raw_to_... [  0%] 0 of 1
[0e/aa1f36] process > organize_output:add_details... [100%] 1 of 1 ✔
[-        ] process > organize_output:add_cleaned... -

executor >  local (51)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [100%] 1 of 1 ✔
[59/7f44c9] process > organize_output:calculate_c... [  0%] 0 of 1
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[-        ] process > organize_output:prepare_cle... -
[ab/1e5f7d] process > organize_output:add_raw_to_... [100%] 1 of 1 ✔
[0e/aa1f36] process > organize_output:add_details... [100%] 1 of 1 ✔
[-        ] process > organize_output:add_cleaned... -

executor >  local (52)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [100%] 1 of 1 ✔
[59/7f44c9] process > organize_output:calculate_c... [100%] 1 of 1 ✔
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[40/11e82b] process > organize_output:prepare_cle... [  0%] 0 of 1
[ab/1e5f7d] process > organize_output:add_raw_to_... [100%] 1 of 1 ✔
[0e/aa1f36] process > organize_output:add_details... [100%] 1 of 1 ✔
[-        ] process > organize_output:add_cleaned... -

executor >  local (53)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [100%] 1 of 1 ✔
[59/7f44c9] process > organize_output:calculate_c... [100%] 1 of 1 ✔
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[40/11e82b] process > organize_output:prepare_cle... [100%] 1 of 1 ✔
[ab/1e5f7d] process > organize_output:add_raw_to_... [100%] 1 of 1 ✔
[0e/aa1f36] process > organize_output:add_details... [100%] 1 of 1 ✔
[42/d58892] process > organize_output:add_cleaned... [100%] 1 of 1 ✔

executor >  local (53)
[5c/ad391a] process > calculate_checksum_on_metaf... [100%] 1 of 1 ✔
[71/c1ce86] process > calculate_checksum_on_sumst... [100%] 1 of 1 ✔
[62/52480d] process > make_metafile_unix_friendly... [100%] 1 of 1 ✔
[ef/29262c] process > check_sumstat_format (1)       [100%] 1 of 1 ✔
[f8/21421c] process > add_sorted_rowindex_to_sums... [100%] 1 of 1 ✔
[77/fdf8f8] process > map_to_dbsnp:prepare_dbsnp_... [100%] 1 of 1 ✔
[94/0e7620] process > map_to_dbsnp:remove_duplica... [100%] 1 of 1 ✔
[e7/ecaf21] process > map_to_dbsnp:maplift_dbsnp_... [100%] 1 of 1 ✔
[0e/1d31af] process > map_to_dbsnp:is_chrpos_diff... [100%] 1 of 1 ✔
[5b/0fbeb5] process > map_to_dbsnp:reformat_chrom... [100%] 2 of 2 ✔
[d4/ec0cc0] process > map_to_dbsnp:detect_genome_... [100%] 8 of 8 ✔
[4a/46e55d] process > map_to_dbsnp:decide_genome_... [100%] 2 of 2 ✔
[0e/9381c9] process > map_to_dbsnp:build_warning (2) [100%] 2 of 2 ✔
[ce/a789c1] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 2 of 2 ✔
[f6/4ef8de] process > map_to_dbsnp:maplift_dbsnp_... [100%] 2 of 2 ✔
[29/00022e] process > map_to_dbsnp:select_chrpos_... [100%] 1 of 1 ✔
[ee/4f3d59] process > map_to_dbsnp:rm_dup_chrpos_... [100%] 1 of 1 ✔
[7a/21fe84] process > map_to_dbsnp:reformat_sumst... [100%] 1 of 1 ✔
[58/0a0c12] process > map_to_dbsnp:split_multiall... [100%] 1 of 1 ✔
[82/2efe9e] process > allele_correction:allele_co... [100%] 1 of 1 ✔
[-        ] process > allele_correction:allele_co... -
[99/9a1333] process > allele_correction:rm_dup_ch... [100%] 1 of 1 ✔
[4d/5f4e06] process > update_stats:numeric_filter... [100%] 1 of 1 ✔
[a7/ee4071] process > update_stats:convert_neglog... [100%] 1 of 1 ✔
[6b/1ece90] process > update_stats:force_eaf (1)     [100%] 1 of 1 ✔
[55/f9fe99] process > update_stats:prep_af_stats (1) [100%] 1 of 1 ✔
[7a/74e21c] process > update_stats:add_af_stats (1)  [100%] 1 of 1 ✔
[90/3a71b5] process > update_stats:infer_stats (2)   [100%] 2 of 2 ✔
[d9/b785b7] process > update_stats:merge_inferred... [100%] 1 of 1 ✔
[df/df07ea] process > update_stats:select_stats_f... [100%] 1 of 1 ✔
[d7/4f2b22] process > organize_output:final_assem... [100%] 1 of 1 ✔
[91/c3e53c] process > organize_output:prep_GRCh37... [100%] 1 of 1 ✔
[aa/c5d9a0] process > organize_output:collect_rmd... [100%] 1 of 1 ✔
[cb/336d0f] process > organize_output:desc_rmd_li... [100%] 1 of 1 ✔
[f9/97c288] process > organize_output:gzip_outfil... [100%] 1 of 1 ✔
[59/7f44c9] process > organize_output:calculate_c... [100%] 1 of 1 ✔
[a4/a5410a] process > organize_output:collect_and... [100%] 1 of 1 ✔
[40/11e82b] process > organize_output:prepare_cle... [100%] 1 of 1 ✔
[ab/1e5f7d] process > organize_output:add_raw_to_... [100%] 1 of 1 ✔
[0e/aa1f36] process > organize_output:add_details... [100%] 1 of 1 ✔
[42/d58892] process > organize_output:add_cleaned... [100%] 1 of 1 ✔
Completed at: 28-Feb-2022 09:56:41
Duration    : 20m 7s
CPU hours   : 0.5
Succeeded   : 53


cp: cannot stat ‘/cluster/work/jobs/13695822/work’: No such file or directory

Task and CPU usage stats:
       JobID    JobName  AllocCPUS   NTasks     MinCPU MinCPUTask     AveCPU    Elapsed ExitCode 
------------ ---------- ---------- -------- ---------- ---------- ---------- ---------- -------- 
13695820_35     SUMSTAT         16                                             00:20:21      1:0 
13695820_35+      batch         16        1   00:37:58          0   00:37:58   00:20:21      1:0 
13695820_35+     extern         16        1   00:00:00          0   00:00:00   00:20:21      0:0 

Memory usage stats:
       JobID     MaxRSS MaxRSSTask     AveRSS MaxPages   MaxPagesTask   AvePages 
------------ ---------- ---------- ---------- -------- -------------- ---------- 
13695820_35                                                                      
13695820_35+   1168452K          0   1168452K        0              0          0 
13695820_35+          0          0          0        0              0          0 

Disk usage stats:
       JobID  MaxDiskRead MaxDiskReadTask    AveDiskRead MaxDiskWrite MaxDiskWriteTask   AveDiskWrite 
------------ ------------ --------------- -------------- ------------ ---------------- -------------- 
13695820_35                                                                                           
13695820_35+        2.77M               0          2.77M        0.30M                0          0.30M 
13695820_35+        0.00M               0          0.00M            0                0              0 

Job 13695822 completed at Mon Feb 28 09:56:42 CET 2022


```