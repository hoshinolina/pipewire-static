if static
  pipewire_dep = declare_dependency(
  dependencies : [pthread_lib, atomic_dep, spa_dep],
  include_directories : [pipewire_inc, configinc],
  variables : {
    'moduledir' : '',
    'confdatadir' : '',
  }
  )
libpipewire_c_args = [
  '-DOLD_MEDIA_SESSION_WORKAROUND=1'
]
if host_machine.system() != 'freebsd' and host_machine.system() != 'midnightbsd'
  libpipewire_c_args += [
    '-D_POSIX_C_SOURCE'
  ]
endif
  subdir('modules')
endif
subdir('pipewire')
if not static
  subdir('modules')
subdir('daemon')
subdir('tools')
subdir('examples')
if get_option('tests').allowed()
  subdir('tests')
endif
endif

if gst_dep.length() != 0
  subdir('gst')
endif
