project('cvi_miniz', 'c')

miniz_includes = include_directories('.')

cfg = configuration_data()
cfg.set('MINIZ_EXPORT', '')
miniz_export_h = configure_file(output: 'miniz_export.h',
                                configuration: cfg)

libcvi_miniz = static_library('cvi_miniz',
                          miniz_export_h, 'miniz.c', 'miniz_zip.c', 'miniz_tinfl.c', 'miniz_tdef.c',
                          include_directories: miniz_includes)

miniz_dependency = declare_dependency(link_with: libcvi_miniz,
                                      include_directories: miniz_includes)
                                      
miniz_dep = miniz_dependency # Compatibility for WrapDB users

if meson.version().version_compare('>= 0.54.0')
    meson.override_dependency('cvi_miniz', miniz_dep)
endif
