
vkd3d_test_flags = []
if vkd3d_platform == 'windows'
  if enable_d3d12
    vkd3d_test_deps = [ lib_d3d12, lib_dxgi, vkd3d_common_dep ]
  else
    vkd3d_test_deps = [ vkd3d_dep, vkd3d_utils_dep ]
    vkd3d_test_flags = ['-DVKD3D_FORCE_UTILS_WRAPPER=1']
  endif
else
  vkd3d_test_deps = [ vkd3d_dep, vkd3d_utils_dep ]
endif

d3d12_test_utils_lib = static_library('d3d12-test-utils', 'd3d12_test_utils.c',
  dependencies        : vkd3d_test_deps,
  include_directories : vkd3d_private_includes,
  override_options    : [ 'c_std='+vkd3d_c_std ])

d3d12_test_src = [
  'd3d12_clip_cull_distance.c',
  'd3d12_geometry_shader.c',
  'd3d12_win32_exclusive.c',
  'd3d12_root_signature.c',
  'd3d12_depth_stencil.c',
  'd3d12_render_target.c',
  'd3d12_tessellation.c',
  'd3d12_sm_advanced.c',
  'd3d12_mesh_shader.c',
  'd3d12_descriptors.c',
  'd3d12_raytracing.c',
  'd3d12_robustness.c',
  'd3d12_streamout.c',
  'd3d12_pso_blob.c',
  'd3d12_resource.c',
  'd3d12_bindless.c',
  'd3d12_shaders.c',
  'd3d12_command.c',
  'd3d12_sparse.c',
  'd3d12_device.c',
  'd3d12_clear.c',
  'd3d12_query.c',
  'd3d12_sync.c',
  'd3d12_copy.c',
  'd3d12_vrs.c',
  'd3d12_pso.c',
  'd3d12_va.c',
  'd3d12.c',
]

executable('d3d12', d3d12_test_src,
  dependencies        : vkd3d_test_deps,
  include_directories : vkd3d_private_includes,
  install             : false,
  c_args              : vkd3d_test_flags,
  override_options    : [ 'c_std='+vkd3d_c_std ],
  link_with           : [ d3d12_test_utils_lib ])

executable('descriptor-performance', 'descriptor_performance.c',
  dependencies        : vkd3d_test_deps,
  include_directories : vkd3d_private_includes,
  install             : false,
  c_args              : vkd3d_test_flags,
  override_options    : [ 'c_std='+vkd3d_c_std ],
  link_with           : [ d3d12_test_utils_lib ])
