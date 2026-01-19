videoconvert_sources = [
  'videoadapter.c',
  'videoconvert-dummy.c',
  'plugin.c'
]

extra_cargs = []
extra_dependencies = []

if avcodec_dep.found() and avutil_dep.found() and swscale_dep.found()
  videoconvert_ffmpeg = static_library('videoconvert_fmmpeg',
    ['videoconvert-ffmpeg.c' ],
    dependencies : [ spa_dep, avcodec_dep, avutil_dep, swscale_dep ],
    install : false
    )
  extra_cargs += '-D HAVE_VIDEOCONVERT_FFMPEG'
  extra_dependencies += videoconvert_ffmpeg
endif

videoconvertlib = library('spa-videoconvert',
  videoconvert_sources,
  c_args : extra_cargs,
  c_static_args: [ '-DSPA_STATIC_PLUGIN="videoconvert/libspa-videoconvert"' ],
  dependencies : [ spa_dep, mathlib ],
  link_with : extra_dependencies,
  install : true,
  install_dir : spa_plugindir / 'videoconvert')

if static
  static_plugins += [videoconvertlib]
endif
