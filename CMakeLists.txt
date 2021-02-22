cmake_minimum_required(VERSION 3.0)

project(SWHPlugins)

set(XML_FILES
  alias_1407.xml
  allpass_1895.xml
  amp_1181.xml
  am_pitchshift_1433.xml
  analogue_osc_1416.xml
  bandpass_a_iir_1893.xml
  bandpass_iir_1892.xml
  bode_shifter_1431.xml
  bode_shifter_cv_1432.xml
  butterworth_1902.xml
  chebstortion_1430.xml
  comb_1190.xml
  comb_1887.xml
  comb_splitter_1411.xml
  const_1909.xml
  crossover_dist_1404.xml
  dc_remove_1207.xml
  debug_1184.xml
  decay_1886.xml
  decimator_1202.xml
  declip_1195.xml
  delay_1898.xml
  delayorama_1402.xml
  diode_1185.xml
  divider_1186.xml
  dj_eq_1901.xml
  dj_flanger_1438.xml
  dyson_compress_1403.xml
  fad_delay_1192.xml
  fast_lookahead_limiter_1913.xml
  flanger_1191.xml
  fm_osc_1415.xml
  foldover_1213.xml
  foverdrive_1196.xml
  freq_tracker_1418.xml
  gate_1410.xml
  gate_1921.xml
  giant_flange_1437.xml
  gong_1424.xml
  gong_beater_1439.xml
  gsm_1215.xml
  gverb_1216.xml
  hard_limiter_1413.xml
  harmonic_gen_1220.xml
  hermes_filter_1200.xml
  highpass_iir_1890.xml
  hilbert_1440.xml
  imp_1199.xml
  impulse_1885.xml
  inv_1429.xml
  karaoke_1409.xml
  latency_1914.xml
  lcr_delay_1436.xml
  lowpass_iir_1891.xml
  ls_filter_1908.xml
  matrix_ms_st_1421.xml
  matrix_spatialiser_1422.xml
  matrix_st_ms_1420.xml
  mbeq_1197.xml
  mod_delay_1419.xml
  multivoice_chorus_1201.xml
  notch_iir_1894.xml
  phasers_1217.xml
  pitch_scale_1193.xml
  pitch_scale_1194.xml
  plate_1423.xml
  pointer_cast_1910.xml
  rate_shifter_1417.xml
  retro_flange_1208.xml
  revdelay_1605.xml
  ringmod_1188.xml
  satan_maximiser_1408.xml
  sc1_1425.xml
  sc2_1426.xml
  sc3_1427.xml
  sc4_1882.xml
  sc4m_1916.xml
  se4_1883.xml
  shaper_1187.xml
  sifter_1210.xml
  sin_cos_1881.xml
  single_para_1203.xml
  sinus_wavewrapper_1198.xml
  smooth_decimate_1414.xml
  split_1406.xml
  step_muxer_1212.xml
  surround_encoder_1401.xml
  svf_1214.xml
  tape_delay_1211.xml
  transient_1206.xml
  triple_para_1204.xml
  valve_1209.xml
  valve_rect_1405.xml
  vocoder_1337.xml
  vynil_1905.xml
  wave_terrain_1412.xml
  xfade_1915.xml
  zm1_1428.xml
)

set(CMAKE_SHARED_MODULE_PREFIX "")

foreach(XML_FILE ${XML_FILES})
  get_filename_component(PLUGIN_NAME ${XML_FILE} NAME_WE)
  execute_process(
    COMMAND perl "${CMAKE_CURRENT_SOURCE_DIR}/makestub.pl" "${CMAKE_CURRENT_SOURCE_DIR}/${XML_FILE}"
    OUTPUT_FILE "${CMAKE_CURRENT_BINARY_DIR}/${PLUGIN_NAME}.c"
  )
  add_library(${PLUGIN_NAME} MODULE "${CMAKE_CURRENT_BINARY_DIR}/${PLUGIN_NAME}.c")
  target_include_directories(${PLUGIN_NAME} PRIVATE .)
endforeach()
